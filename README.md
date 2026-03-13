import { useState, useEffect, useRef } from "react";

// ── DATOS ────────────────────────────────────────────────────────
const COUNTRIES = [
  { id:"ae", name:"Emiratos Árabes", flag:"🇦🇪", region:"Medio Oriente", currency:"AED", incomeTax:0,  corporateTax:9,  vat:5,  rent:2800, color:"#F59E0B", lat:24.4,  lng:54.4  },
  { id:"pt", name:"Portugal",        flag:"🇵🇹", region:"Europa",         currency:"EUR", incomeTax:20, corporateTax:21, vat:23, rent:1200, color:"#10B981", lat:38.7,  lng:-9.1  },
  { id:"es", name:"España",          flag:"🇪🇸", region:"Europa",         currency:"EUR", incomeTax:47, corporateTax:25, vat:21, rent:1400, color:"#EF4444", lat:40.4,  lng:-3.7  },
  { id:"sg", name:"Singapur",        flag:"🇸🇬", region:"Asia",           currency:"SGD", incomeTax:22, corporateTax:17, vat:9,  rent:3500, color:"#6366F1", lat:1.35,  lng:103.8 },
  { id:"mx", name:"México",          flag:"🇲🇽", region:"Latinoamérica",  currency:"MXN", incomeTax:35, corporateTax:30, vat:16, rent:700,  color:"#F97316", lat:19.4,  lng:-99.1 },
  { id:"ge", name:"Georgia",         flag:"🇬🇪", region:"Cáucaso",        currency:"GEL", incomeTax:20, corporateTax:15, vat:18, rent:600,  color:"#EC4899", lat:41.7,  lng:44.8  },
  { id:"pa", name:"Panamá",          flag:"🇵🇦", region:"Centroamérica",  currency:"USD", incomeTax:0,  corporateTax:25, vat:7,  rent:900,  color:"#06B6D4", lat:8.9,   lng:-79.5 },
  { id:"th", name:"Tailandia",       flag:"🇹🇭", region:"Asia",           currency:"THB", incomeTax:35, corporateTax:20, vat:7,  rent:600,  color:"#8B5CF6", lat:13.7,  lng:100.5 },
  { id:"ee", name:"Estonia",         flag:"🇪🇪", region:"Europa",         currency:"EUR", incomeTax:20, corporateTax:0,  vat:22, rent:900,  color:"#0EA5E9", lat:59.4,  lng:24.7  },
  { id:"uy", name:"Uruguay",         flag:"🇺🇾", region:"Latinoamérica",  currency:"UYU", incomeTax:7,  corporateTax:25, vat:22, rent:800,  color:"#14B8A6", lat:-34.9, lng:-56.2 },
];

const ORIGIN_COUNTRIES = [
  { id:"es_origin", name:"España",       flag:"🇪🇸", incomeTax:47, corporateTax:25, rent:1400, color:"#EF4444" },
  { id:"de",        name:"Alemania",     flag:"🇩🇪", incomeTax:45, corporateTax:30, rent:1600, color:"#FBBF24" },
  { id:"fr",        name:"Francia",      flag:"🇫🇷", incomeTax:45, corporateTax:25, rent:1500, color:"#60A5FA" },
  { id:"uk",        name:"Reino Unido",  flag:"🇬🇧", incomeTax:45, corporateTax:25, rent:1800, color:"#A78BFA" },
  { id:"it",        name:"Italia",       flag:"🇮🇹", incomeTax:43, corporateTax:24, rent:1100, color:"#34D399" },
  { id:"ar",        name:"Argentina",    flag:"🇦🇷", incomeTax:35, corporateTax:35, rent:400,  color:"#FB923C" },
];

// ── CLAUDE API ───────────────────────────────────────────────────
async function callClaude(prompt, system, webSearch = false) {
  const body = {
    model: "claude-sonnet-4-20250514",
    max_tokens: 800,
    system,
    messages: [{ role: "user", content: prompt }],
  };
  if (webSearch) body.tools = [{ type: "web_search_20250305", name: "web_search" }];
  const res = await fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(body),
  });
  const data = await res.json();
  return data.content?.map(b => b.text || "").filter(Boolean).join("") || "";
}

// ── ANIMACIÓN CONTADOR ───────────────────────────────────────────
function useCounter(target, duration = 1200) {
  const [val, setVal] = useState(0);
  useEffect(() => {
    if (!target) return;
    let start = null;
    const step = (ts) => {
      if (!start) start = ts;
      const prog = Math.min((ts - start) / duration, 1);
      const ease = 1 - Math.pow(1 - prog, 3);
      setVal(Math.round(ease * target));
      if (prog < 1) requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  }, [target]);
  return val;
}

// ── MAPA SVG MUNDIAL SIMPLIFICADO ───────────────────────────────
const MAP_DOTS = [
  // Europe
  { id:"pt", x:197, y:168 }, { id:"es", x:205, y:165 }, { id:"fr", x:218, y:158 },
  { id:"de", x:228, y:150 }, { id:"it", x:232, y:163 }, { id:"ee", x:248, y:136 },
  // Americas
  { id:"mx", x:95,  y:192 }, { id:"pa", x:115, y:210 }, { id:"uy", x:140, y:275 },
  { id:"ar", x:132, y:270 },
  // Asia/ME
  { id:"ae", x:313, y:185 }, { id:"ge", x:293, y:160 }, { id:"sg", x:372, y:222 },
  { id:"th", x:365, y:200 },
];

function WorldMap({ selectedId, hoveredId, onSelect, onHover, countries }) {
  return (
    <div style={{ position:"relative", width:"100%", paddingBottom:"52%", background:"rgba(255,255,255,0.02)", borderRadius:20, overflow:"hidden", border:"1px solid rgba(255,255,255,0.06)" }}>
      <svg viewBox="0 0 500 260" style={{ position:"absolute", inset:0, width:"100%", height:"100%" }}>
        {/* Simplified world outline paths */}
        <path d="M30,120 Q60,100 90,110 Q120,95 150,105 Q180,95 200,100 Q220,90 250,95 Q280,85 310,90 Q340,80 370,85 Q400,80 430,90 Q460,85 480,95 L480,200 Q450,195 420,200 Q390,205 360,200 Q330,195 300,200 Q270,205 240,195 Q210,200 180,195 Q150,200 120,195 Q90,200 60,190 Q40,195 30,200 Z" fill="rgba(255,255,255,0.03)" stroke="rgba(255,255,255,0.06)" strokeWidth="0.5"/>
        {/* Grid lines */}
        {[130,160,190,220].map(y => <line key={y} x1="20" y1={y} x2="480" y2={y} stroke="rgba(255,255,255,0.03)" strokeWidth="0.5"/>)}
        {[100,160,220,280,340,400,460].map(x => <line key={x} x1={x} y1="80" x2={x} y2="240" stroke="rgba(255,255,255,0.03)" strokeWidth="0.5"/>)}

        {/* Country dots */}
        {MAP_DOTS.map(dot => {
          const country = countries.find(c => c.id === dot.id || (dot.id === "fr" && c.id === "fr") || (dot.id === "de" && c.id === "de") || (dot.id === "ar" && c.id === "ar"));
          const destCountry = COUNTRIES.find(c => c.id === dot.id);
          const isSelected = selectedId === dot.id;
          const isHovered = hoveredId === dot.id;
          const col = destCountry?.color || "#ffffff";
          const hasData = COUNTRIES.find(c => c.id === dot.id);

          return (
            <g key={dot.id} style={{ cursor: hasData ? "pointer" : "default" }}
              onClick={() => hasData && onSelect(dot.id)}
              onMouseEnter={() => onHover(dot.id)}
              onMouseLeave={() => onHover(null)}>
              {(isSelected || isHovered) && (
                <circle cx={dot.x} cy={dot.y} r={isSelected ? 14 : 10} fill={col} opacity="0.12">
                  <animate attributeName="r" values={isSelected?"12;18;12":"10;14;10"} dur="2s" repeatCount="indefinite"/>
                </circle>
              )}
              <circle cx={dot.x} cy={dot.y} r={isSelected ? 6 : isHovered ? 5 : 3.5}
                fill={hasData ? col : "rgba(255,255,255,0.2)"}
                stroke={isSelected ? "white" : "transparent"}
                strokeWidth="1.5"
                style={{ transition:"r 0.2s, fill 0.2s" }} />
              {(isSelected || isHovered) && (
                <text x={dot.x} y={dot.y - 10} textAnchor="middle" fill="white" fontSize="7" fontWeight="bold">
                  {destCountry?.flag}
                </text>
              )}
            </g>
          );
        })}
      </svg>
    </div>
  );
}

// ── CALCULADORA DE AHORRO ────────────────────────────────────────
function SavingsCalculator() {
  const [income, setIncome] = useState(80000);
  const [origin, setOrigin] = useState(ORIGIN_COUNTRIES[0]);
  const [dest, setDest] = useState(COUNTRIES[0]);
  const [hoveredId, setHoveredId] = useState(null);
  const [showAll, setShowAll] = useState(false);

  const originTax = Math.round(income * origin.incomeTax / 100);
  const destTax = Math.round(income * dest.incomeTax / 100);
  const annualSaving = originTax - destTax;
  const monthlySaving = Math.round(annualSaving / 12);
  const fiveYearSaving = annualSaving * 5;
  const rentSaving = Math.round((origin.rent - dest.rent) * 12);
  const totalAnnual = annualSaving + Math.max(rentSaving, 0);

  const animatedAnnual = useCounter(Math.max(annualSaving, 0));
  const animatedFive = useCounter(Math.max(fiveYearSaving, 0));

  const ranked = [...COUNTRIES].map(c => ({
    ...c,
    saving: Math.round(income * (origin.incomeTax - c.incomeTax) / 100),
  })).sort((a, b) => b.saving - a.saving);

  return (
    <div style={{ fontFamily:"'Outfit', sans-serif" }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');
        @keyframes fadeUp { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }
        @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.5} }
        @keyframes glow { 0%,100%{box-shadow:0 0 20px rgba(16,185,129,0.3)} 50%{box-shadow:0 0 40px rgba(16,185,129,0.6)} }
        .fade-up { animation: fadeUp 0.5s ease forwards; }
        input[type=range] { -webkit-appearance:none; width:100%; height:4px; border-radius:99px; background:rgba(255,255,255,0.08); outline:none; }
        input[type=range]::-webkit-slider-thumb { -webkit-appearance:none; width:20px; height:20px; border-radius:50%; background:linear-gradient(135deg,#7c3aed,#4f46e5); cursor:pointer; box-shadow:0 0 0 3px rgba(124,58,237,0.25); }
        select { appearance:none; -webkit-appearance:none; background:rgba(255,255,255,0.05); border:1px solid rgba(255,255,255,0.1); color:white; border-radius:10px; padding:8px 12px; font-family:'Outfit',sans-serif; font-size:13px; cursor:pointer; outline:none; }
        .country-btn:hover { transform:scale(1.02); border-color:rgba(255,255,255,0.2) !important; }
        .country-btn { transition: all 0.18s ease; }
      `}</style>

      {/* SECCIÓN 1 — CALCULADORA */}
      <div style={{ background:"radial-gradient(ellipse 80% 60% at 20% 50%, rgba(15,5,40,0.98) 0%, transparent 65%), radial-gradient(ellipse 60% 50% at 80% 30%, rgba(5,10,40,0.95) 0%, transparent 60%), #020208", minHeight:"100vh", padding:"40px 24px" }}>

        <div style={{ maxWidth:900, margin:"0 auto" }}>
          {/* Header */}
          <div style={{ textAlign:"center", marginBottom:48 }}>
            <div style={{ display:"inline-flex", alignItems:"center", gap:6, padding:"4px 14px", borderRadius:99, background:"rgba(16,185,129,0.1)", border:"1px solid rgba(16,185,129,0.25)", color:"#34d399", fontSize:11, fontWeight:600, marginBottom:20 }}>
              <span style={{ width:6, height:6, borderRadius:"50%", background:"#34d399", display:"inline-block", animation:"pulse 1.5s ease infinite" }}/>
              CALCULADORA DE AHORRO FISCAL
            </div>
            <h1 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(2rem,5vw,3.8rem)", lineHeight:1, color:"white", marginBottom:14 }}>
              Descubre cuánto<br/>
              <span style={{ background:"linear-gradient(135deg,#34d399,#60a5fa)", WebkitBackgroundClip:"text", WebkitTextFillColor:"transparent" }}>
                ahorrarías al año.
              </span>
            </h1>
            <p style={{ color:"rgba(255,255,255,0.4)", fontSize:16, maxWidth:440, margin:"0 auto" }}>
              Compara tu fiscalidad actual con cualquier destino del mundo en tiempo real.
            </p>
          </div>

          {/* Controles */}
          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:16, marginBottom:24 }}>
            <div style={{ background:"rgba(255,255,255,0.04)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
              <label style={{ color:"rgba(255,255,255,0.35)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:8 }}>Ingresos anuales</label>
              <div style={{ color:"white", fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:28, marginBottom:12 }}>€{income.toLocaleString()}</div>
              <input type="range" min="20000" max="500000" step="5000" value={income} onChange={e => setIncome(+e.target.value)} />
              <div style={{ display:"flex", justifyContent:"space-between", marginTop:4 }}>
                <span style={{ color:"rgba(255,255,255,0.2)", fontSize:10 }}>€20K</span>
                <span style={{ color:"rgba(255,255,255,0.2)", fontSize:10 }}>€500K</span>
              </div>
            </div>
            <div style={{ background:"rgba(255,255,255,0.04)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
              <label style={{ color:"rgba(255,255,255,0.35)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:8 }}>País de origen</label>
              <select value={origin.id} onChange={e => setOrigin(ORIGIN_COUNTRIES.find(c => c.id === e.target.value))} style={{ width:"100%", marginBottom:8 }}>
                {ORIGIN_COUNTRIES.map(c => <option key={c.id} value={c.id}>{c.flag} {c.name}</option>)}
              </select>
              <div style={{ display:"flex", gap:8 }}>
                <div style={{ flex:1, background:"rgba(239,68,68,0.1)", borderRadius:10, padding:"8px 10px", border:"1px solid rgba(239,68,68,0.2)" }}>
                  <div style={{ color:"rgba(255,255,255,0.35)", fontSize:9 }}>IRPF actual</div>
                  <div style={{ color:"#f87171", fontWeight:700, fontSize:16 }}>{origin.incomeTax}%</div>
                </div>
                <div style={{ flex:1, background:"rgba(239,68,68,0.1)", borderRadius:10, padding:"8px 10px", border:"1px solid rgba(239,68,68,0.2)" }}>
                  <div style={{ color:"rgba(255,255,255,0.35)", fontSize:9 }}>Pagas ahora</div>
                  <div style={{ color:"#f87171", fontWeight:700, fontSize:16 }}>€{originTax.toLocaleString()}</div>
                </div>
              </div>
            </div>
          </div>

          {/* Resultado principal */}
          <div style={{ borderRadius:24, padding:"32px 28px", marginBottom:24, position:"relative", overflow:"hidden", animation:"glow 3s ease infinite", background:"linear-gradient(135deg, rgba(16,185,129,0.12) 0%, rgba(96,165,250,0.08) 100%)", border:"1px solid rgba(16,185,129,0.3)" }}>
            <div style={{ position:"absolute", top:-40, right:-40, width:160, height:160, borderRadius:"50%", background:"rgba(16,185,129,0.06)", pointerEvents:"none" }} />
            <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr", gap:20, textAlign:"center" }}>
              <div>
                <div style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, marginBottom:6 }}>Ahorras este año en {dest.name}</div>
                <div style={{ color:"#34d399", fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,3rem)", lineHeight:1 }}>
                  €{animatedAnnual.toLocaleString()}
                </div>
                <div style={{ color:"rgba(52,211,153,0.5)", fontSize:11, marginTop:4 }}>€{monthlySaving.toLocaleString()}/mes</div>
              </div>
              <div>
                <div style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, marginBottom:6 }}>En 5 años</div>
                <div style={{ color:"#60a5fa", fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,3rem)", lineHeight:1 }}>
                  €{animatedFive.toLocaleString()}
                </div>
                <div style={{ color:"rgba(96,165,250,0.5)", fontSize:11, marginTop:4 }}>acumulado</div>
              </div>
              <div>
                <div style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, marginBottom:6 }}>IRPF destino</div>
                <div style={{ color: dest.incomeTax === 0 ? "#34d399" : dest.incomeTax < 25 ? "#60a5fa" : "#fbbf24", fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,3rem)", lineHeight:1 }}>
                  {dest.incomeTax}%
                </div>
                <div style={{ color:"rgba(255,255,255,0.3)", fontSize:11, marginTop:4 }}>
                  {dest.incomeTax === 0 ? "🎯 Cero impuestos" : `vs ${origin.incomeTax}% actual`}
                </div>
              </div>
            </div>
          </div>

          {/* Mapa + ranking */}
          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:16 }}>
            {/* Mapa */}
            <div style={{ background:"rgba(255,255,255,0.02)", borderRadius:20, padding:16, border:"1px solid rgba(255,255,255,0.06)" }}>
              <div style={{ color:"rgba(255,255,255,0.35)", fontSize:11, textTransform:"uppercase", letterSpacing:1, marginBottom:10 }}>🗺️ Selecciona destino en el mapa</div>
              <WorldMap
                selectedId={dest.id}
                hoveredId={hoveredId}
                onSelect={id => { const c = COUNTRIES.find(x => x.id === id); if(c) setDest(c); }}
                onHover={setHoveredId}
                countries={COUNTRIES}
              />
              <div style={{ marginTop:12, display:"flex", alignItems:"center", gap:10, padding:"10px 14px", borderRadius:12, background:`${dest.color}15`, border:`1px solid ${dest.color}35` }}>
                <span style={{ fontSize:24 }}>{dest.flag}</span>
                <div>
                  <div style={{ color:"white", fontWeight:600, fontSize:13 }}>{dest.name}</div>
                  <div style={{ color:"rgba(255,255,255,0.4)", fontSize:10 }}>IRPF {dest.incomeTax}% · IS {dest.corporateTax}% · IVA {dest.vat}%</div>
                </div>
              </div>
            </div>

            {/* Ranking */}
            <div style={{ background:"rgba(255,255,255,0.02)", borderRadius:20, padding:16, border:"1px solid rgba(255,255,255,0.06)" }}>
              <div style={{ color:"rgba(255,255,255,0.35)", fontSize:11, textTransform:"uppercase", letterSpacing:1, marginBottom:10 }}>🏆 Ranking de ahorro vs {origin.name}</div>
              <div style={{ display:"flex", flexDirection:"column", gap:6 }}>
                {(showAll ? ranked : ranked.slice(0, 6)).map((c, i) => {
                  const pct = Math.max(c.saving / (income * 0.5) * 100, 0);
                  const isSelected = c.id === dest.id;
                  return (
                    <div key={c.id} onClick={() => setDest(c)} className="country-btn"
                      style={{ display:"flex", alignItems:"center", gap:10, padding:"8px 10px", borderRadius:12, cursor:"pointer", border:`1px solid ${isSelected ? c.color+"60" : "rgba(255,255,255,0.04)"}`, background: isSelected ? `${c.color}12` : "rgba(255,255,255,0.02)" }}>
                      <span style={{ color:"rgba(255,255,255,0.25)", fontSize:10, fontWeight:700, width:14 }}>{i+1}</span>
                      <span style={{ fontSize:16 }}>{c.flag}</span>
                      <div style={{ flex:1, minWidth:0 }}>
                        <div style={{ color:"rgba(255,255,255,0.8)", fontSize:11, fontWeight:500 }}>{c.name}</div>
                        <div style={{ height:3, borderRadius:99, background:"rgba(255,255,255,0.06)", marginTop:3, overflow:"hidden" }}>
                          <div style={{ height:"100%", borderRadius:99, width:`${pct}%`, background:c.saving > 0 ? c.color : "#ef4444" }} />
                        </div>
                      </div>
                      <div style={{ textAlign:"right", flexShrink:0 }}>
                        <div style={{ color: c.saving > 0 ? "#34d399" : "#f87171", fontWeight:700, fontSize:12 }}>
                          {c.saving > 0 ? "+" : ""}€{c.saving.toLocaleString()}
                        </div>
                        <div style={{ color:"rgba(255,255,255,0.25)", fontSize:9 }}>{c.incomeTax}% IRPF</div>
                      </div>
                    </div>
                  );
                })}
                {!showAll && ranked.length > 6 && (
                  <button onClick={() => setShowAll(true)} style={{ padding:"7px", borderRadius:10, border:"1px dashed rgba(255,255,255,0.1)", background:"transparent", color:"rgba(255,255,255,0.35)", cursor:"pointer", fontSize:11 }}>
                    Ver {ranked.length - 6} más →
                  </button>
                )}
              </div>
            </div>
          </div>

          {/* Disclaimer */}
          <div style={{ marginTop:16, padding:"8px 14px", borderRadius:10, background:"rgba(245,158,11,0.05)", border:"1px solid rgba(245,158,11,0.12)" }}>
            <p style={{ color:"rgba(255,255,255,0.25)", fontSize:10, margin:0, lineHeight:1.5 }}>⚠️ Cálculo orientativo basado en tipos marginales máximos. No constituye asesoramiento fiscal. Consulta con un profesional antes de tomar decisiones.</p>
          </div>
        </div>
      </div>
    </div>
  );
}

// ── INFORME PDF (generado en browser con HTML → print) ───────────
function PDFReport() {
  const [income, setIncome] = useState(80000);
  const [dest, setDest] = useState(COUNTRIES[0]);
  const [origin, setOrigin] = useState(ORIGIN_COUNTRIES[0]);
  const [loading, setLoading] = useState(false);
  const [aiAnalysis, setAiAnalysis] = useState("");
  const [generated, setGenerated] = useState(false);
  const reportRef = useRef(null);

  const annualSaving = Math.round(income * (origin.incomeTax - dest.incomeTax) / 100);
  const fiveYear = annualSaving * 5;

  const generateAnalysis = async () => {
    setLoading(true);
    setGenerated(false);
    try {
      const text = await callClaude(
        `Genera un análisis ejecutivo breve (4 párrafos concisos) para un empresario que quiere mudarse de ${origin.name} a ${dest.name} con ingresos de €${income.toLocaleString()}/año. Incluye: 1) Ahorro fiscal estimado (${annualSaving > 0 ? `€${annualSaving.toLocaleString()}` : "incremento de costes"}), 2) Ventajas principales del destino, 3) Pasos inmediatos recomendados, 4) Advertencia de riesgos. Tono profesional, datos concretos, en español.`,
        "Eres asesor de movilidad internacional de REZZOW PRO. Responde siempre en español con datos concretos y tono ejecutivo. Máximo 200 palabras.",
        true
      );
      setAiAnalysis(text);
      setGenerated(true);
    } catch {
      setAiAnalysis("Error al generar. Verifica tu conexión.");
      setGenerated(true);
    }
    setLoading(false);
  };

  const printReport = () => {
    const printWindow = window.open("", "_blank");
    const date = new Date().toLocaleDateString("es-ES", { day:"2-digit", month:"long", year:"numeric" });
    printWindow.document.write(`
      <!DOCTYPE html>
      <html lang="es">
      <head>
        <meta charset="UTF-8"/>
        <title>Informe REZZOW — ${dest.name}</title>
        <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
        <style>
          * { margin:0; padding:0; box-sizing:border-box; }
          body { font-family:'Outfit', sans-serif; background:#fff; color:#111; }
          .page { padding:48px 56px; max-width:800px; margin:0 auto; }
          .header { display:flex; justify-content:space-between; align-items:flex-start; padding-bottom:24px; border-bottom:3px solid #7c3aed; margin-bottom:32px; }
          .logo { font-family:'Syne', sans-serif; font-size:28px; font-weight:800; color:#7c3aed; }
          .logo span { font-size:11px; background:#7c3aed; color:white; padding:2px 8px; border-radius:99px; margin-left:8px; vertical-align:middle; }
          .meta { text-align:right; font-size:12px; color:#666; }
          .title { font-family:'Syne', sans-serif; font-size:32px; font-weight:800; color:#111; margin-bottom:6px; }
          .subtitle { color:#666; font-size:15px; margin-bottom:32px; }
          .hero { background:linear-gradient(135deg, #f0fdf4, #eff6ff); border-radius:16px; padding:28px; margin-bottom:28px; border:1px solid #d1fae5; }
          .hero-grid { display:grid; grid-template-columns:1fr 1fr 1fr; gap:20px; text-align:center; }
          .hero-num { font-family:'Syne', sans-serif; font-size:36px; font-weight:800; }
          .hero-label { font-size:11px; color:#666; text-transform:uppercase; letter-spacing:1px; margin-bottom:6px; }
          .section { margin-bottom:28px; }
          .section-title { font-family:'Syne', sans-serif; font-size:16px; font-weight:700; color:#7c3aed; margin-bottom:14px; padding-bottom:6px; border-bottom:1px solid #e5e7eb; }
          .grid-2 { display:grid; grid-template-columns:1fr 1fr; gap:14px; }
          .stat-box { background:#f9fafb; border-radius:12px; padding:14px 16px; border:1px solid #e5e7eb; }
          .stat-label { font-size:10px; color:#999; text-transform:uppercase; letter-spacing:0.5px; margin-bottom:3px; }
          .stat-val { font-size:18px; font-weight:700; color:#111; }
          .analysis { background:#fafafa; border-radius:12px; padding:20px; border-left:4px solid #7c3aed; font-size:13px; line-height:1.7; color:#333; white-space:pre-wrap; }
          .disclaimer { margin-top:40px; padding:14px 16px; background:#fffbeb; border-radius:10px; border:1px solid #fde68a; font-size:10px; color:#92400e; line-height:1.5; }
          .footer { margin-top:32px; padding-top:16px; border-top:1px solid #e5e7eb; display:flex; justify-content:space-between; font-size:10px; color:#999; }
          .badge { display:inline-block; padding:3px 10px; border-radius:99px; font-size:11px; font-weight:600; }
          .saving { color:#059669; } .cost { color:#dc2626; }
          @media print { .page { padding:32px 40px; } }
        </style>
      </head>
      <body>
        <div class="page">
          <div class="header">
            <div>
              <div class="logo">REZZOW<span>PRO</span></div>
              <div style="font-size:12px;color:#666;margin-top:4px">Plataforma de Movilidad Internacional</div>
            </div>
            <div class="meta">
              <div style="font-weight:600;margin-bottom:2px">Informe de Reubicación</div>
              <div>${date}</div>
              <div style="margin-top:4px;color:#7c3aed;font-weight:600">CONFIDENCIAL</div>
            </div>
          </div>

          <div class="title">${dest.flag} Análisis: ${origin.name} → ${dest.name}</div>
          <div class="subtitle">Basado en ingresos anuales de €${income.toLocaleString()}</div>

          <div class="hero">
            <div class="hero-grid">
              <div>
                <div class="hero-label">Ahorro fiscal anual</div>
                <div class="hero-num ${annualSaving > 0 ? "saving" : "cost"}">
                  ${annualSaving > 0 ? "+" : ""}€${annualSaving.toLocaleString()}
                </div>
              </div>
              <div>
                <div class="hero-label">En 5 años</div>
                <div class="hero-num saving">€${fiveYear.toLocaleString()}</div>
              </div>
              <div>
                <div class="hero-label">IRPF destino</div>
                <div class="hero-num" style="color:${dest.incomeTax === 0 ? "#059669" : "#2563eb"}">${dest.incomeTax}%</div>
              </div>
            </div>
          </div>

          <div class="section">
            <div class="section-title">Comparativa Fiscal</div>
            <div class="grid-2">
              <div class="stat-box">
                <div class="stat-label">IRPF ${origin.name}</div>
                <div class="stat-val" style="color:#dc2626">${origin.incomeTax}%</div>
                <div style="font-size:11px;color:#999;margin-top:2px">Pagas €${Math.round(income * origin.incomeTax / 100).toLocaleString()}/año</div>
              </div>
              <div class="stat-box">
                <div class="stat-label">IRPF ${dest.name}</div>
                <div class="stat-val" style="color:#059669">${dest.incomeTax}%</div>
                <div style="font-size:11px;color:#999;margin-top:2px">Pagarías €${Math.round(income * dest.incomeTax / 100).toLocaleString()}/año</div>
              </div>
              <div class="stat-box">
                <div class="stat-label">Impuesto sociedades ${dest.name}</div>
                <div class="stat-val">${dest.corporateTax}%</div>
              </div>
              <div class="stat-box">
                <div class="stat-label">IVA / VAT ${dest.name}</div>
                <div class="stat-val">${dest.vat}%</div>
              </div>
            </div>
          </div>

          ${aiAnalysis ? `
          <div class="section">
            <div class="section-title">Análisis Ejecutivo IA</div>
            <div class="analysis">${aiAnalysis}</div>
          </div>
          ` : ""}

          <div class="disclaimer">
            ⚠️ Este informe es orientativo y ha sido generado con ayuda de inteligencia artificial. Los datos fiscales son aproximados y pueden variar según circunstancias personales, convenios de doble imposición y legislación vigente. REZZOW no presta servicios de asesoramiento legal ni fiscal. Consulta siempre con un profesional cualificado antes de tomar decisiones de reubicación o inversión.
          </div>

          <div class="footer">
            <span>REZZOW PRO · rezzow.com · ${date}</span>
            <span>Generado con IA · Datos orientativos</span>
          </div>
        </div>
        <script>window.onload = () => window.print();</script>
      </body>
      </html>
    `);
    printWindow.document.close();
  };

  return (
    <div style={{ background:"radial-gradient(ellipse at 70% 30%, rgba(124,58,237,0.12) 0%, transparent 60%), #020208", minHeight:"100vh", padding:"40px 24px", fontFamily:"'Outfit', sans-serif" }}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap'); select { appearance:none; background:rgba(255,255,255,0.05); border:1px solid rgba(255,255,255,0.1); color:white; border-radius:10px; padding:8px 12px; font-family:'Outfit',sans-serif; font-size:13px; cursor:pointer; outline:none; width:100%; } input[type=range] { -webkit-appearance:none; width:100%; height:4px; border-radius:99px; background:rgba(255,255,255,0.08); outline:none; } input[type=range]::-webkit-slider-thumb { -webkit-appearance:none; width:18px; height:18px; border-radius:50%; background:linear-gradient(135deg,#7c3aed,#4f46e5); cursor:pointer; }`}</style>
      <div style={{ maxWidth:700, margin:"0 auto" }}>
        <div style={{ textAlign:"center", marginBottom:36 }}>
          <div style={{ display:"inline-flex", alignItems:"center", gap:6, padding:"4px 14px", borderRadius:99, background:"rgba(124,58,237,0.12)", border:"1px solid rgba(124,58,237,0.25)", color:"#a78bfa", fontSize:11, fontWeight:600, marginBottom:16 }}>📄 INFORME PDF PERSONALIZADO</div>
          <h2 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,3rem)", color:"white", lineHeight:1.1, marginBottom:10 }}>Tu informe de reubicación<br/><span style={{ background:"linear-gradient(135deg,#a78bfa,#60a5fa)", WebkitBackgroundClip:"text", WebkitTextFillColor:"transparent" }}>en 30 segundos.</span></h2>
          <p style={{ color:"rgba(255,255,255,0.4)", fontSize:14 }}>Análisis personalizado con IA · Listo para imprimir o enviar a tu gestor</p>
        </div>

        {/* Config */}
        <div style={{ background:"rgba(255,255,255,0.03)", borderRadius:20, padding:24, border:"1px solid rgba(255,255,255,0.07)", marginBottom:20 }}>
          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:14, marginBottom:14 }}>
            <div>
              <label style={{ color:"rgba(255,255,255,0.35)", fontSize:11, display:"block", marginBottom:6 }}>País de origen</label>
              <select value={origin.id} onChange={e => setOrigin(ORIGIN_COUNTRIES.find(c => c.id === e.target.value))}>
                {ORIGIN_COUNTRIES.map(c => <option key={c.id} value={c.id}>{c.flag} {c.name}</option>)}
              </select>
            </div>
            <div>
              <label style={{ color:"rgba(255,255,255,0.35)", fontSize:11, display:"block", marginBottom:6 }}>País destino</label>
              <select value={dest.id} onChange={e => setDest(COUNTRIES.find(c => c.id === e.target.value))}>
                {COUNTRIES.map(c => <option key={c.id} value={c.id}>{c.flag} {c.name}</option>)}
              </select>
            </div>
          </div>
          <div>
            <label style={{ color:"rgba(255,255,255,0.35)", fontSize:11, display:"block", marginBottom:6 }}>Ingresos anuales: <strong style={{ color:"white" }}>€{income.toLocaleString()}</strong></label>
            <input type="range" min="20000" max="500000" step="5000" value={income} onChange={e => setIncome(+e.target.value)} />
          </div>
        </div>

        {/* Preview del informe */}
        <div ref={reportRef} style={{ background:"white", borderRadius:20, padding:"28px 32px", marginBottom:20, color:"#111" }}>
          <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", paddingBottom:16, borderBottom:"3px solid #7c3aed", marginBottom:20 }}>
            <div>
              <div style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:22, color:"#7c3aed" }}>REZZOW <span style={{ fontSize:10, background:"#7c3aed", color:"white", padding:"2px 7px", borderRadius:99 }}>PRO</span></div>
              <div style={{ fontSize:11, color:"#999", marginTop:2 }}>Plataforma de Movilidad Internacional</div>
            </div>
            <div style={{ textAlign:"right", fontSize:11, color:"#999" }}>
              <div style={{ fontWeight:600, color:"#111" }}>Informe de Reubicación</div>
              <div>{new Date().toLocaleDateString("es-ES", { day:"2-digit", month:"long", year:"numeric" })}</div>
            </div>
          </div>
          <div style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:22, marginBottom:4 }}>{dest.flag} {origin.name} → {dest.name}</div>
          <div style={{ color:"#666", fontSize:12, marginBottom:20 }}>Ingresos anuales: €{income.toLocaleString()}</div>

          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr", gap:14, marginBottom:20 }}>
            {[[annualSaving > 0 ? `+€${annualSaving.toLocaleString()}` : `€${annualSaving.toLocaleString()}`, "Ahorro anual", annualSaving > 0 ? "#059669" : "#dc2626"],[`€${fiveYear.toLocaleString()}`, "En 5 años", "#2563eb"],[`${dest.incomeTax}%`, "IRPF destino", "#7c3aed"]].map(([val,lbl,col]) => (
              <div key={lbl} style={{ background:"#f9fafb", borderRadius:12, padding:"14px 16px", border:"1px solid #e5e7eb", textAlign:"center" }}>
                <div style={{ fontSize:10, color:"#999", textTransform:"uppercase", letterSpacing:0.5, marginBottom:4 }}>{lbl}</div>
                <div style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:22, color:col }}>{val}</div>
              </div>
            ))}
          </div>

          {generated && aiAnalysis ? (
            <div style={{ background:"#fafafa", borderRadius:12, padding:16, borderLeft:"4px solid #7c3aed", fontSize:12, lineHeight:1.7, color:"#333", whiteSpace:"pre-wrap" }}>{aiAnalysis}</div>
          ) : (
            <div style={{ background:"#f3f4f6", borderRadius:12, padding:16, textAlign:"center", color:"#999", fontSize:12 }}>
              {loading ? "⏳ Generando análisis IA..." : "Haz clic en 'Generar análisis' para añadir el análisis IA"}
            </div>
          )}

          <div style={{ marginTop:16, padding:"10px 14px", background:"#fffbeb", borderRadius:8, border:"1px solid #fde68a", fontSize:10, color:"#92400e", lineHeight:1.5 }}>
            ⚠️ Informe orientativo generado con IA. No constituye asesoramiento fiscal ni legal. Consulta con un profesional antes de tomar decisiones.
          </div>
        </div>

        <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:12 }}>
          <button onClick={generateAnalysis} disabled={loading}
            style={{ padding:"14px", borderRadius:14, border:"1px solid rgba(124,58,237,0.4)", background:"rgba(124,58,237,0.15)", color:"white", fontSize:13, fontWeight:600, cursor:"pointer", opacity:loading?0.6:1 }}>
            {loading ? "⏳ Generando..." : "✨ Generar análisis IA"}
          </button>
          <button onClick={printReport}
            style={{ padding:"14px", borderRadius:14, border:"none", background:"linear-gradient(135deg,#7c3aed,#4f46e5)", color:"white", fontSize:13, fontWeight:600, cursor:"pointer" }}>
            📄 Descargar PDF
          </button>
        </div>
        <p style={{ color:"rgba(255,255,255,0.2)", fontSize:10, textAlign:"center", marginTop:10 }}>El PDF se abre en una nueva pestaña listo para guardar o imprimir</p>
      </div>
    </div>
  );
}

// ── ALERTAS DE EMAIL ─────────────────────────────────────────────
function EmailAlerts() {
  const [email, setEmail] = useState("");
  const [selected, setSelected] = useState(["ae","pt","es"]);
  const [types, setTypes] = useState(["fiscal","visados","economia"]);
  const [freq, setFreq] = useState("weekly");
  const [submitted, setSubmitted] = useState(false);

  const alertTypes = [
    { id:"fiscal",    label:"⚖️ Cambios fiscales",    desc:"Nuevos impuestos, deducciones, tipos" },
    { id:"visados",   label:"🛂 Actualizaciones visados", desc:"Nuevos requisitos, plazos, precios" },
    { id:"economia",  label:"📊 Alertas económicas",  desc:"PIB, inflación, tipo de cambio" },
    { id:"legal",     label:"📜 Cambios legales",      desc:"Nueva regulación empresarial" },
    { id:"mercado",   label:"💼 Mercado laboral",      desc:"Salarios, demanda, permisos" },
  ];

  const toggleCountry = id => setSelected(p => p.includes(id) ? p.filter(x=>x!==id) : [...p, id]);
  const toggleType = id => setTypes(p => p.includes(id) ? p.filter(x=>x!==id) : [...p, id]);

  if (submitted) return (
    <div style={{ background:"#020208", minHeight:"100vh", display:"flex", alignItems:"center", justifyContent:"center", fontFamily:"'Outfit', sans-serif" }}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap'); @keyframes fadeUp{from{opacity:0;transform:translateY(30px)}to{opacity:1;transform:translateY(0)}} .fade{animation:fadeUp 0.6s ease forwards}`}</style>
      <div className="fade" style={{ textAlign:"center", padding:40 }}>
        <div style={{ fontSize:72, marginBottom:20 }}>🎉</div>
        <h2 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:32, color:"white", marginBottom:12 }}>¡Alertas activadas!</h2>
        <p style={{ color:"rgba(255,255,255,0.5)", fontSize:15, maxWidth:360, margin:"0 auto 24px", lineHeight:1.6 }}>
          Recibirás notificaciones en <strong style={{ color:"white" }}>{email}</strong> sobre cambios en {selected.length} países.
        </p>
        <div style={{ display:"flex", flexWrap:"wrap", gap:8, justifyContent:"center" }}>
          {selected.map(id => {
            const c = COUNTRIES.find(x=>x.id===id);
            return c ? <span key={id} style={{ padding:"6px 14px", borderRadius:99, background:`${c.color}20`, border:`1px solid ${c.color}40`, color:"white", fontSize:12 }}>{c.flag} {c.name}</span> : null;
          })}
        </div>
      </div>
    </div>
  );

  return (
    <div style={{ background:"radial-gradient(ellipse at 30% 70%, rgba(16,185,129,0.08) 0%, transparent 55%), #020208", minHeight:"100vh", padding:"40px 24px", fontFamily:"'Outfit', sans-serif" }}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap'); input[type=email],input[type=text]{background:rgba(255,255,255,0.05);border:1px solid rgba(255,255,255,0.1);color:white;border-radius:12px;padding:12px 16px;font-family:'Outfit',sans-serif;font-size:14px;outline:none;width:100%;} input:focus{border-color:rgba(124,58,237,0.5);}`}</style>
      <div style={{ maxWidth:640, margin:"0 auto" }}>
        <div style={{ textAlign:"center", marginBottom:36 }}>
          <div style={{ display:"inline-flex", alignItems:"center", gap:6, padding:"4px 14px", borderRadius:99, background:"rgba(16,185,129,0.1)", border:"1px solid rgba(16,185,129,0.25)", color:"#34d399", fontSize:11, fontWeight:600, marginBottom:16 }}>
            <span style={{ width:6, height:6, borderRadius:"50%", background:"#34d399", display:"inline-block", animation:"pulse 1.5s ease infinite" }}/>
            🔔 ALERTAS DE CAMBIOS LEGALES
            <style>{`@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}`}</style>
          </div>
          <h2 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,2.8rem)", color:"white", lineHeight:1.1, marginBottom:10 }}>
            Entérate antes<br/>
            <span style={{ background:"linear-gradient(135deg,#34d399,#60a5fa)", WebkitBackgroundClip:"text", WebkitTextFillColor:"transparent" }}>que tu competencia.</span>
          </h2>
          <p style={{ color:"rgba(255,255,255,0.4)", fontSize:14 }}>Recibe alertas instantáneas cuando cambien impuestos, visados o regulación en tus países.</p>
        </div>

        <div style={{ display:"flex", flexDirection:"column", gap:16 }}>
          {/* Email */}
          <div style={{ background:"rgba(255,255,255,0.03)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
            <label style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:10 }}>Tu email</label>
            <input type="email" placeholder="tu@empresa.com" value={email} onChange={e => setEmail(e.target.value)} />
          </div>

          {/* Países */}
          <div style={{ background:"rgba(255,255,255,0.03)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
            <label style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:12 }}>Países a monitorizar ({selected.length})</label>
            <div style={{ display:"grid", gridTemplateColumns:"repeat(auto-fill,minmax(120px,1fr))", gap:8 }}>
              {COUNTRIES.map(c => {
                const on = selected.includes(c.id);
                return (
                  <button key={c.id} onClick={() => toggleCountry(c.id)}
                    style={{ padding:"8px 10px", borderRadius:12, border:`1px solid ${on ? c.color+"60" : "rgba(255,255,255,0.06)"}`, background: on ? `${c.color}18` : "transparent", color: on ? "white" : "rgba(255,255,255,0.4)", cursor:"pointer", fontSize:11, fontWeight: on ? 600 : 400, transition:"all 0.15s" }}>
                    {c.flag} {c.name}
                  </button>
                );
              })}
            </div>
          </div>

          {/* Tipos */}
          <div style={{ background:"rgba(255,255,255,0.03)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
            <label style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:12 }}>Tipo de alertas</label>
            <div style={{ display:"flex", flexDirection:"column", gap:8 }}>
              {alertTypes.map(t => {
                const on = types.includes(t.id);
                return (
                  <button key={t.id} onClick={() => toggleType(t.id)}
                    style={{ display:"flex", alignItems:"center", gap:12, padding:"10px 14px", borderRadius:12, border:`1px solid ${on ? "rgba(124,58,237,0.4)" : "rgba(255,255,255,0.06)"}`, background: on ? "rgba(124,58,237,0.12)" : "transparent", cursor:"pointer", textAlign:"left", transition:"all 0.15s" }}>
                    <div style={{ width:18, height:18, borderRadius:5, border:`2px solid ${on ? "#7c3aed" : "rgba(255,255,255,0.2)"}`, background: on ? "#7c3aed" : "transparent", display:"flex", alignItems:"center", justifyContent:"center", flexShrink:0, fontSize:10, color:"white" }}>{on ? "✓" : ""}</div>
                    <div>
                      <div style={{ color:"rgba(255,255,255,0.85)", fontSize:12, fontWeight:500 }}>{t.label}</div>
                      <div style={{ color:"rgba(255,255,255,0.3)", fontSize:10 }}>{t.desc}</div>
                    </div>
                  </button>
                );
              })}
            </div>
          </div>

          {/* Frecuencia */}
          <div style={{ background:"rgba(255,255,255,0.03)", borderRadius:18, padding:20, border:"1px solid rgba(255,255,255,0.07)" }}>
            <label style={{ color:"rgba(255,255,255,0.4)", fontSize:11, textTransform:"uppercase", letterSpacing:1, display:"block", marginBottom:12 }}>Frecuencia</label>
            <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr 1fr", gap:8 }}>
              {[["instant","⚡ Inmediata","Cada cambio"],["daily","📅 Diaria","Resumen diario"],["weekly","📬 Semanal","Resumen semanal"]].map(([v,l,d]) => (
                <button key={v} onClick={() => setFreq(v)}
                  style={{ padding:"10px 8px", borderRadius:12, border:`1px solid ${freq===v ? "rgba(124,58,237,0.5)" : "rgba(255,255,255,0.06)"}`, background: freq===v ? "rgba(124,58,237,0.15)" : "transparent", color: freq===v ? "white" : "rgba(255,255,255,0.45)", cursor:"pointer", textAlign:"center" }}>
                  <div style={{ fontSize:12, fontWeight:600 }}>{l}</div>
                  <div style={{ fontSize:9, marginTop:2, color:"rgba(255,255,255,0.3)" }}>{d}</div>
                </button>
              ))}
            </div>
          </div>

          <button onClick={() => email && selected.length && setSubmitted(true)} disabled={!email || !selected.length}
            style={{ padding:"16px", borderRadius:16, border:"none", background: email && selected.length ? "linear-gradient(135deg,#7c3aed,#4f46e5)" : "rgba(255,255,255,0.06)", color: email && selected.length ? "white" : "rgba(255,255,255,0.25)", fontSize:15, fontWeight:700, cursor: email && selected.length ? "pointer" : "not-allowed", fontFamily:"'Syne', sans-serif" }}>
            🔔 Activar alertas →
          </button>
          <p style={{ color:"rgba(255,255,255,0.2)", fontSize:10, textAlign:"center" }}>Sin spam · Cancela cuando quieras · Los emails simulan el comportamiento real</p>
        </div>
      </div>
    </div>
  );
}

// ── APP PRINCIPAL ─────────────────────────────────────────────────
export default function App() {
  const [tab, setTab] = useState("calc");

  const TABS = [
    { id:"calc",   label:"💰 Calculadora",  desc:"Ahorro fiscal" },
    { id:"map",    label:"🗺️ Mapa",          desc:"Explorar países" },
    { id:"pdf",    label:"📄 Informe PDF",   desc:"Descargable" },
    { id:"alerts", label:"🔔 Alertas",       desc:"Cambios legales" },
  ];

  return (
    <div style={{ background:"#020208", minHeight:"100vh", fontFamily:"'Outfit', sans-serif" }}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap'); * { box-sizing:border-box; margin:0; padding:0; } ::-webkit-scrollbar{width:4px} ::-webkit-scrollbar-thumb{background:rgba(255,255,255,0.1);border-radius:2px}`}</style>

      {/* Nav */}
      <nav style={{ position:"sticky", top:0, zIndex:100, background:"rgba(2,2,8,0.92)", backdropFilter:"blur(20px)", borderBottom:"1px solid rgba(255,255,255,0.06)", padding:"0 20px" }}>
        <div style={{ maxWidth:960, margin:"0 auto", display:"flex", alignItems:"center", gap:0 }}>
          <div style={{ display:"flex", alignItems:"center", gap:8, padding:"14px 0", marginRight:24 }}>
            <div style={{ width:30, height:30, borderRadius:8, background:"linear-gradient(135deg,#7c3aed,#4f46e5)", display:"flex", alignItems:"center", justifyContent:"center", fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:14, color:"white" }}>R</div>
            <span style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:17, color:"white" }}>REZZOW</span>
            <span style={{ fontSize:9, padding:"2px 7px", borderRadius:99, background:"rgba(124,58,237,0.2)", border:"1px solid rgba(124,58,237,0.3)", color:"rgba(196,181,253,0.9)", fontWeight:600 }}>PRO</span>
          </div>
          {TABS.map(t => (
            <button key={t.id} onClick={() => setTab(t.id)}
              style={{ padding:"16px 14px", background:"transparent", border:"none", cursor:"pointer", fontSize:12, fontWeight: tab===t.id ? 600 : 400, color: tab===t.id ? "white" : "rgba(255,255,255,0.4)", borderBottom: tab===t.id ? "2px solid #7c3aed" : "2px solid transparent", transition:"all 0.15s", whiteSpace:"nowrap" }}>
              {t.label}
            </button>
          ))}
        </div>
      </nav>

      {/* Content */}
      {tab === "calc" && <SavingsCalculator />}
      {tab === "map" && <MapExplorer />}
      {tab === "pdf" && <PDFReport />}
      {tab === "alerts" && <EmailAlerts />}
    </div>
  );
}

// ── MAPA EXPLORADOR COMPLETO ──────────────────────────────────────
function MapExplorer() {
  const [selected, setSelected] = useState(null);
  const [hovered, setHovered] = useState(null);
  const country = COUNTRIES.find(c => c.id === selected);

  return (
    <div style={{ background:"radial-gradient(ellipse at 50% 40%, rgba(99,102,241,0.1) 0%, transparent 60%), #020208", minHeight:"100vh", padding:"40px 24px", fontFamily:"'Outfit', sans-serif" }}>
      <style>{`@import url('https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500;600&display=swap');`}</style>
      <div style={{ maxWidth:960, margin:"0 auto" }}>
        <div style={{ textAlign:"center", marginBottom:32 }}>
          <div style={{ display:"inline-flex", alignItems:"center", gap:6, padding:"4px 14px", borderRadius:99, background:"rgba(99,102,241,0.12)", border:"1px solid rgba(99,102,241,0.25)", color:"#a5b4fc", fontSize:11, fontWeight:600, marginBottom:16 }}>🗺️ MAPA MUNDIAL INTERACTIVO</div>
          <h2 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:"clamp(1.8rem,4vw,3rem)", color:"white", lineHeight:1.1, marginBottom:8 }}>Explora el mundo,<br/><span style={{ background:"linear-gradient(135deg,#a5b4fc,#60a5fa)", WebkitBackgroundClip:"text", WebkitTextFillColor:"transparent" }}>elige tu próximo hogar.</span></h2>
          <p style={{ color:"rgba(255,255,255,0.35)", fontSize:13 }}>Haz clic en cualquier punto del mapa para ver los datos fiscales del país</p>
        </div>

        <WorldMap selectedId={selected} hoveredId={hovered} onSelect={id => setSelected(selected===id?null:id)} onHover={setHovered} countries={COUNTRIES} />

        {/* Datos del país seleccionado */}
        {country ? (
          <div style={{ marginTop:20, borderRadius:20, padding:24, border:`1px solid ${country.color}40`, background:`linear-gradient(135deg, ${country.color}10 0%, rgba(8,8,22,0.95) 100%)`, animation:"fadeUp 0.4s ease" }}>
            <style>{`@keyframes fadeUp{from{opacity:0;transform:translateY(15px)}to{opacity:1;transform:translateY(0)}}`}</style>
            <div style={{ display:"flex", alignItems:"center", gap:16, marginBottom:20 }}>
              <span style={{ fontSize:48 }}>{country.flag}</span>
              <div>
                <h3 style={{ fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:24, color:"white" }}>{country.name}</h3>
                <p style={{ color:"rgba(255,255,255,0.4)", fontSize:12 }}>{country.region} · {country.currency}</p>
              </div>
              <button onClick={() => setSelected(null)} style={{ marginLeft:"auto", background:"rgba(255,255,255,0.06)", border:"1px solid rgba(255,255,255,0.1)", color:"rgba(255,255,255,0.5)", borderRadius:10, padding:"6px 12px", cursor:"pointer", fontSize:11 }}>✕ Cerrar</button>
            </div>
            <div style={{ display:"grid", gridTemplateColumns:"repeat(4,1fr)", gap:12 }}>
              {[[`${country.incomeTax}%`,"IRPF",country.incomeTax===0?"#34d399":country.incomeTax<25?"#60a5fa":"#f87171"],[`${country.corporateTax}%`,"Soc.",country.corporateTax<20?"#34d399":"#fbbf24"],[`${country.vat}%`,"IVA","#a78bfa"],[`€${country.rent}`,"Alq./mes","#60a5fa"]].map(([v,l,col]) => (
                <div key={l} style={{ background:"rgba(255,255,255,0.04)", borderRadius:14, padding:"14px 10px", border:"1px solid rgba(255,255,255,0.06)", textAlign:"center" }}>
                  <div style={{ color:"rgba(255,255,255,0.35)", fontSize:10, marginBottom:4 }}>{l}</div>
                  <div style={{ color:col, fontFamily:"'Syne', sans-serif", fontWeight:800, fontSize:22 }}>{v}</div>
                </div>
              ))}
            </div>
          </div>
        ) : (
          <div style={{ marginTop:20, display:"flex", flexWrap:"wrap", gap:8, justifyContent:"center" }}>
            {COUNTRIES.map(c => (
              <button key={c.id} onClick={() => setSelected(c.id)}
                style={{ padding:"7px 14px", borderRadius:99, border:`1px solid ${c.color}40`, background:`${c.color}12`, color:"white", cursor:"pointer", fontSize:12, transition:"all 0.15s" }}
                onMouseEnter={e => { e.currentTarget.style.transform="scale(1.05)"; e.currentTarget.style.borderColor=c.color; }}
                onMouseLeave={e => { e.currentTarget.style.transform="scale(1)"; e.currentTarget.style.borderColor=`${c.color}40`; }}>
                {c.flag} {c.name}
              </button>
            ))}
          </div>
        )}
      </div>
    </div>
  );
}
