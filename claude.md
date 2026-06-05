This is a quartz project. It has its own style. However, I want to put this in a subdomain for my main webpage, and I want it to imitate the style as much as possible (without breaking anything).

This shows the style of my original page:

<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trayectoria — Variante A</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400;0,500;0,600;1,400;1,500&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#f4efe6;
    --paper-2:#efe8db;
    --ink:#211d17;
    --ink-soft:#5a5247;
    --rule:#c8bca6;
    --accent:#7c2d2d;     /* rojo tinta para trayectoria */
    --accent-2:#3b5d50;   /* verde apagado para intereses */
    --gold:#9a7b3f;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{
    background:var(--paper);
    color:var(--ink);
    font-family:'EB Garamond',Garamond,'Times New Roman',serif;
    font-size:19px;
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
    background-image:radial-gradient(circle at 20% 10%, rgba(255,255,255,.5), transparent 40%);
  }
  .wrap{max-width:1140px;margin:0 auto;padding:0 32px}
 
  header.cover{
    text-align:center;
    padding:110px 0 70px;
    border-bottom:1px solid var(--rule);
  }
  header.cover .kicker{
    font-variant:small-caps;
    letter-spacing:.32em;
    font-size:.8rem;
    color:var(--gold);
    margin-bottom:22px;
  }
  header.cover h1{
    font-weight:500;
    font-size:clamp(2.6rem,6vw,4.2rem);
    line-height:1.05;
    letter-spacing:.01em;
  }
  header.cover .sub{
    margin-top:20px;
    font-style:italic;
    font-size:1.25rem;
    color:var(--ink-soft);
  }
  header.cover .intro{
    max-width:62ch;
    margin:40px auto 0;
    text-align:left;
    font-size:1.16rem;
    line-height:1.72;
  }
  header.cover .intro p{margin-bottom:18px;color:var(--ink-soft)}
  header.cover .intro p:first-child{color:var(--ink)}
  header.cover .intro .cta{margin:26px 0}
  header.cover .intro .cta a{
    font-style:normal;
    font-variant:small-caps;
    letter-spacing:.14em;
    font-size:.95rem;
    border:1px solid var(--accent);
    color:var(--accent);
    padding:9px 22px;
    border-radius:999px;
    text-decoration:none;
    transition:background .25s ease,color .25s ease;
    display:inline-block;
  }
  header.cover .intro .cta a:hover{background:var(--accent);color:var(--paper)}
  header.cover .intro .more{
    font-style:italic;
    color:var(--gold);
    margin-top:30px;
    margin-bottom:0;
  }
  header.cover .intro a{
    color:var(--accent);
    text-decoration:none;
    border-bottom:1px solid var(--rule);
    transition:border-color .25s ease;
  }
  header.cover .intro a:hover{border-color:var(--accent)}
  header.cover .legend{
    margin-top:46px;
    display:flex;gap:40px;justify-content:center;
    font-variant:small-caps;letter-spacing:.18em;font-size:.82rem;
  }
  header.cover .legend span{display:inline-flex;align-items:center;gap:9px}
  .dot{width:9px;height:9px;border-radius:50%;display:inline-block}
  .dot.t{background:var(--accent)}
  .dot.i{background:var(--accent-2)}
 
  /* timeline */
  .tl{position:relative;padding:80px 0 120px}
  .tl::before{
    content:"";position:absolute;top:0;bottom:0;left:50%;
    width:1px;background:var(--rule);transform:translateX(-50%);
  }
  .row{
    position:relative;
    display:grid;
    grid-template-columns:1fr 120px 1fr;
    align-items:start;
    margin-bottom:84px;
  }
  .year-node{
    grid-column:2;
    display:flex;flex-direction:column;align-items:center;
    position:relative;
  }
  .year-node .yr{
    background:var(--paper);
    border:1px solid var(--rule);
    border-radius:999px;
    padding:8px 4px;width:84px;text-align:center;
    font-size:1.45rem;font-weight:600;letter-spacing:.02em;
    color:var(--ink);
    box-shadow:0 1px 0 #fff inset;
    z-index:2;
  }
  .col{padding-top:6px}
  .col.left{grid-column:1;text-align:right;padding-right:42px}
  .col.right{grid-column:3;text-align:left;padding-left:42px}
  .col h3{
    font-variant:small-caps;letter-spacing:.2em;font-size:.78rem;
    font-weight:600;margin-bottom:14px;
  }
  .col.left h3{color:var(--accent-2)}
  .col.right h3{color:var(--accent)}
  .col p{margin-bottom:9px;color:var(--ink-soft)}
  .col p:first-of-type{color:var(--ink)}
  .col em{color:var(--ink)}
 
  /* connectors */
  .row::after{
    content:"";position:absolute;top:14px;left:50%;width:8px;height:8px;
    border-radius:50%;background:var(--gold);transform:translateX(-50%);
    box-shadow:0 0 0 4px var(--paper);z-index:1;
  }
 
  /* reveal */
  .row{opacity:0;transform:translateY(26px);transition:opacity .8s ease, transform .8s ease}
  .row.in{opacity:1;transform:none}
 
  footer{
    text-align:center;padding:60px 0 90px;border-top:1px solid var(--rule);
    color:var(--ink-soft);font-style:italic;
  }
 
  @media(max-width:760px){
    body{font-size:17px}
    .tl::before{left:26px}
    .row{grid-template-columns:52px 1fr;gap:10px;margin-bottom:54px}
    .year-node{grid-column:1;align-items:flex-start}
    .year-node .yr{width:auto;padding:5px 10px;font-size:1.05rem}
    .row::after{left:26px}
    .col.left,.col.right{grid-column:2;text-align:left;padding:0 0 0 12px}
    .col.left{margin-bottom:22px}
  }
</style>
</head>
<body>
  <div class="wrap">
    <header class="cover">
      <div class="kicker">2014 — 2025</div>
      <h1>Juan Zaragoza</h1>
      <div class="intro">
        <p>Me dedico a estudiar cómo funcionan los sistemas fundamentales de cooperación, porque creo que encierran la clave para enfrentar las grandes crisis de la actualidad.</p>
        <p>Parte de lo que aprendí está en <a href="https://filosofiadelfuturo.com">filosofiadelfuturo.com</a> y <a href="https://txt.networkismo.com">txt.networkismo.com</a>, aunque mucho permanece inédito. En 2026 quiero terminar de publicar algunas conclusiones y continuar experimentando métodos para escalar la cooperación horizontal.</p>
        <p>Recientemente escribí un ensayo sobre el problema más importante que quiero resolver, y es quizás mi mejor forma de presentarme.</p>
        <p class="cta"><a href="#">Leer el ensayo</a></p>
        <p class="more">Más abajo podés ver mi recorrido.</p>
      </div>
    </header>
 
    <section class="tl" id="tl"></section>
 
    <footer>fin · 2025</footer>
  </div>
 
<script>
const TIMELINE = [
  {"year":2014,"trayectoria":"<p>Egresé del colegio San Andrés, el colegio británico más antiguo de Sudamérica.</p><p>Allí, obtuve el mejor promedio en los exámenes del diploma IB</p><p>También obtuve el premio al mejor rendimiento en Física</p><p>Fui el presidente más jóven del Student Council (primero del penúltimo año en la historia del colegio)</p>","intereses":"<p>Durante el colegio, consideraba injusto y nocivo al sistema económico, pero encontraba que la principal teoría para cambiarlo (el marxismo) tenía problemas críticos.</p><p>Me propuse encontrar una teoría actualizada que ayudara a evitar los fracasos políticos y las tendencias autoritarias de las revoluciones.&nbsp;</p><p>Desde la adolescencia, entender mejor la sociedad para lograr transformarla es lo que orienta mi vida</p><p>Decidí estudiar filosofía porque su generalidad parecía de ayuda, y porque Marx se había formado en filosofía.</p>"},
  {"year":2015,"trayectoria":"<p>Cursé el ciclo básico de Filosofía en la Universidad de Buenos Aires</p><p>Me dediqué brevemente a la música pop</p><p>Dos canciones que escribí superaron el millón de reproducciones</p><p>Mi banda obtuvo la segunda canción más viral del verano en Spotify</p>","intereses":"<p>Mi búsqueda partía de un problema: la interpretación marxista de cómo los procesos materiales determinan la cultura era muy lineal.&nbsp;</p><p>Intuía que los errores predictivos de la lucha de clases, incluido el fracaso de las revoluciones, nacían de ahí.&nbsp;</p><p>Como la relación entre el cerebro y la mente parecía importante, decidí estudiar psicología al año siguiente.</p><p>Comencé a leer manuales de cualquier disciplina que ayudara a entender la sociedad</p>"},
];
 
</script>
<script>
  const tl=document.getElementById('tl');
  TIMELINE.forEach(d=>{
    const row=document.createElement('div');
    row.className='row';
    row.innerHTML=`
      <div class="col left">
        <h3>Intereses</h3>
        ${d.intereses}
      </div>
      <div class="year-node"><div class="yr">${d.year}</div></div>
      <div class="col right">
        <h3>Trayectoria</h3>
        ${d.trayectoria}
      </div>`;
    tl.appendChild(row);
  });
  const io=new IntersectionObserver(es=>{
    es.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');io.unobserve(e.target)}})
  },{threshold:.12});
  document.querySelectorAll('.row').forEach(r=>io.observe(r));
</script>
</body>
</html>

I want the whole 