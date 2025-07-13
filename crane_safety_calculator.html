<!DOCTYPE html>
<html lang='en'>
<head>
  <meta charset='UTF-8'>
  <meta name='viewport' content='width=device-width,initial-scale=1.0'>
  <title>Crane Slope Safety Calculator</title>
  <style>
    *{box-sizing:border-box;font-family:Arial,Helvetica,sans-serif}
    body{margin:0;padding:2rem;background:#f5f7fa;color:#222}
    h1{margin-top:0;font-size:1.8rem;text-align:center}
    .wrapper{max-width:960px;margin:0 auto}
    .controls,.results{display:flex;flex-wrap:wrap;gap:1rem;margin:1rem 0;padding:1rem;background:#fff;border-radius:8px;box-shadow:0 2px 4px rgba(0,0,0,.1)}
    .controls label{flex:1 1 200px;display:flex;flex-direction:column;font-weight:600;font-size:.9rem}
    .controls input{margin-top:.25rem;padding:.4rem;border:1px solid #bbb;border-radius:4px;font-size:1rem}
    button{padding:.6rem 1.2rem;border:none;border-radius:4px;background:#0077ff;color:#fff;font-size:1rem;cursor:pointer;align-self:flex-end;transition:background .2s}
    button:hover{background:#005dda}
    .results p{margin:.25rem 0;font-size:1rem;flex:1 1 200px}
    .results span{font-weight:700}
    #diagram{width:100%;max-width:100%;border:1px solid #ddd;border-radius:8px;background:#e8f0ff}
    .note{font-size:.8rem;color:#555;text-align:center;margin-top:1rem}
  </style>
</head>
<body>
  <div class='wrapper'>
    <h1>Crane – Slope Safety Calculator</h1>

    <!-- INPUTS -->
    <form class='controls' id='inputForm' onsubmit='event.preventDefault();calculate()'>
      <label>
        Foundation (Mat) Width W (m)
        <input type='number' id='matWidth' step='0.01' min='0' value='0.9' required>
      </label>
      <label>
        Horizontal Slope Length d (m)
        <input type='number' id='slopeLength' step='0.1' min='0' value='6' required>
      </label>
      <label>
        Vertical Slope Height H (m)
        <input type='number' id='slopeHeight' step='0.1' min='0' value='4' required>
      </label>
      <button type='submit'>Calculate</button>
    </form>

    <!-- OUTPUTS -->
    <div class='results' id='resultsBox'>
      <p>Minimum safe distance D: <span id='outD'>–</span> m</p>
      <p>Status (D ≥ 4W &amp; D + d ≥ 2H): <span id='outStatus'>–</span></p>
    </div>

    <!-- DIAGRAM -->
    <svg id='diagram' viewBox='0 0 800 400' preserveAspectRatio='xMidYMid meet'></svg>

    <p class='note'>Calculated in accordance with BS 7121‑3:2000 &amp; CIRIA C703. For preliminary guidance only – always consult a qualified engineer on site‑specific conditions.</p>
  </div>

<script>
(function(){
  const svgNS = 'http://www.w3.org/2000/svg';

  function createLine(x1,y1,x2,y2,opts={}){
    const l=document.createElementNS(svgNS,'line');
    l.setAttribute('x1',x1);l.setAttribute('y1',y1);l.setAttribute('x2',x2);l.setAttribute('y2',y2);
    l.setAttribute('stroke',opts.stroke||'black');
    l.setAttribute('stroke-width',opts.sw||2);
    if(opts.dash) l.setAttribute('stroke-dasharray',opts.dash);
    return l;
  }

  function createRect(x,y,w,h,opts={}){
    const r=document.createElementNS(svgNS,'rect');
    r.setAttribute('x',x);r.setAttribute('y',y);r.setAttribute('width',w);r.setAttribute('height',h);
    r.setAttribute('fill',opts.fill||'orange');
    r.setAttribute('stroke',opts.stroke||'black');
    return r;
  }

  function clearChildren(el){ while(el.firstChild) el.removeChild(el.firstChild); }

  window.calculate = function(){
    const W=parseFloat(document.getElementById('matWidth').value);
    const d=parseFloat(document.getElementById('slopeLength').value);
    const H=parseFloat(document.getElementById('slopeHeight').value);
    if([W,d,H].some(v=>isNaN(v)||v<0)) return;

    const D1=4*W;
    const D2=Math.max(0,2*H - d);
    const D= Math.max(D1,D2);

    // Update outputs
    document.getElementById('outD').textContent = D.toFixed(2);
    const pass = (D>=D1) && (D + d >= 2*H);
    document.getElementById('outStatus').textContent = pass ? 'PASS' : 'FAIL';
    document.getElementById('outStatus').style.color = pass ? 'green' : 'red';

    // Update diagram
    drawDiagram(W,d,H,D);
  };

  function drawDiagram(W,d,H,D){
    const svg=document.getElementById('diagram');
    clearChildren(svg);

    const scale=40; // pixels per metre
    const groundY=300;
    const originX=50; // left margin

    // Crane pad & crane simple representation
    const padWidth=W*scale;
    const padX=originX;
    const padY=groundY-20;
    svg.appendChild(createRect(padX,padY,padWidth,20,{fill:'#ffd580'}));
    svg.appendChild(createRect(padX+padWidth/2-10,padY-60,20,60,{fill:'#666'})); // mast
    svg.appendChild(createLine(padX+padWidth/2-10,padY-60,padX+padWidth/2+120,padY-160,{sw:4})); // boom

    // Danger distance D indicator
    const Dpx=D*scale;
    svg.appendChild(createLine(padX+padWidth,groundY,padX+padWidth+Dpx,groundY,{stroke:'#00f',dash:'4 4'}));

    // Slope line
    const slopeStartX=padX+padWidth+Dpx;
    const slopeEndX=slopeStartX+d*scale;
    const slopeEndY=groundY+H*scale;
    svg.appendChild(createLine(slopeStartX,groundY,slopeEndX,slopeEndY,{stroke:'#964B00'}));

    // Ground lines
    svg.appendChild(createLine(0,groundY,originX-5,groundY)); // left ground
    svg.appendChild(createLine(slopeEndX, slopeEndY, slopeEndX+100, slopeEndY)); // right ground

    // Labels (simple)
    addText(`D = ${D.toFixed(2)} m`, padX+padWidth + Dpx/2, groundY - 6);
    addText('d', slopeStartX + (slopeEndX-slopeStartX)/2, groundY + 14);
    addText('H', slopeEndX + 14, groundY + (slopeEndY-groundY)/2);

    function addText(t,x,y){
      const txt=document.createElementNS(svgNS,'text');
      txt.setAttribute('x',x);txt.setAttribute('y',y);
      txt.setAttribute('font-size','12');
      txt.setAttribute('text-anchor','middle');
      txt.textContent=t;svg.appendChild(txt);}
  }

  // Initial calculation on load
  calculate();
})();
</script>
</body>
</html>
