<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<title>Holzfäller 3D</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{--panel:rgba(246,240,224,.94);--ink:#2b2118;--mute:#6d5f4d;--gold:#a8730a;--line:#d9ceb2;--btn:#2f6b45;--btnink:#fff;--dis:#b9b29d;--alt:#f6f0e0;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){color-scheme:dark;--panel:rgba(34,49,40,.94);--ink:#eadfc8;--mute:#a99f8a;--gold:#e3b04a;--line:#34473b;--btn:#6fc28a;--btnink:#10261a;--dis:#46564b;--alt:#223128}}
:root[data-theme="dark"]{color-scheme:dark;--panel:rgba(34,49,40,.94);--ink:#eadfc8;--mute:#a99f8a;--gold:#e3b04a;--line:#34473b;--btn:#6fc28a;--btnink:#10261a;--dis:#46564b;--alt:#223128}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent;-webkit-touch-callout:none}
html,body{height:100%;margin:0;overflow:hidden;overscroll-behavior:none;touch-action:manipulation;-webkit-user-select:none;user-select:none;background:#a9cfe6;font-family:'Fredoka','Trebuchet MS',system-ui,sans-serif;color:var(--ink)}
@media (prefers-color-scheme:dark){html,body{background:#131c26}}
#c{position:fixed;inset:0;width:100%;height:100%;display:block;touch-action:none}
.hud{position:fixed;top:0;left:0;right:0;padding:calc(env(safe-area-inset-top,0px) + 8px) 10px 0;display:grid;grid-template-columns:repeat(3,1fr);gap:8px;pointer-events:none}
.stat{background:var(--panel);border:2px solid var(--line);border-radius:14px;padding:6px 10px}
.stat small{display:block;color:var(--mute);font-size:.75rem}
.stat b{font-size:1.2rem;font-weight:600}
.money b{color:var(--gold)}
.stat.full{border-color:var(--gold)}
.msg{position:fixed;left:10px;right:10px;bottom:calc(env(safe-area-inset-bottom,0px) + 10px);background:var(--panel);border-radius:12px;padding:8px 12px;font-size:.95rem;min-height:2.6em;display:flex;align-items:center;pointer-events:none}
#joy{position:fixed;left:20px;bottom:calc(env(safe-area-inset-bottom,0px) + 74px);width:124px;height:124px;border-radius:50%;background:rgba(255,255,255,.2);border:2px solid rgba(255,255,255,.55);touch-action:none;display:flex;align-items:center;justify-content:center}
#knob{width:56px;height:56px;border-radius:50%;background:rgba(255,255,255,.75);box-shadow:0 2px 8px rgba(0,0,0,.3);pointer-events:none}
button.act{font-family:inherit;font-size:1rem;font-weight:600;border:0;border-radius:14px;min-height:54px;padding:8px;background:var(--btn);color:var(--btnink);cursor:pointer}
button.act:disabled{background:var(--dis);color:var(--panel);cursor:not-allowed}
button.act.alt{background:var(--alt);color:var(--ink);border:2px solid var(--btn)}
button:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
.sheet{position:fixed;left:0;right:0;bottom:0;background:var(--panel);border-radius:22px 22px 0 0;padding:14px 12px calc(env(safe-area-inset-bottom,0px) + 14px);max-height:75%;overflow:auto;transform:translateY(105%);transition:transform .25s;box-shadow:0 -6px 24px rgba(0,0,0,.25);z-index:5}
.sheet.open{transform:none}
.sheet h2{margin:0 0 10px;font-size:1.15rem;font-weight:600}
#sell{width:100%;margin-bottom:10px}
.item{display:flex;align-items:center;gap:10px;border:2px solid var(--line);border-radius:14px;padding:8px 10px;margin-bottom:8px}
.item .ic{font-size:1.7rem}
.item .tx{flex:1;min-width:0}
.item .tx b{display:block;font-weight:600}
.item .tx span{color:var(--mute);font-size:.85rem}
.item button{min-width:92px;min-height:48px}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:8px}
@media (prefers-reduced-motion:reduce){.sheet{transition:none}}
</style>
</head>
<body>
<canvas id="c"></canvas>
<div class="hud">
  <div class="stat money"><small>Geld</small><b id="money">0 €</b></div>
  <div class="stat" id="bagBox"><small>Rucksack</small><b id="bag">0 / 3</b></div>
  <div class="stat"><small>Lager</small><b id="pile">0</b></div>
</div>
<div id="joy" aria-label="Steuerung"><div id="knob"></div></div>
<div class="msg" id="msg" aria-live="polite">Laufe mit dem Stick. Tippe auf einen Baum, den Markt oder das Lager.</div>
<div class="sheet" id="sheet">
  <h2>Markt</h2>
  <button class="act" id="sell">Holz verkaufen</button>
  <div id="shop"></div>
  <div class="row2"><button class="act alt" id="reset">Neustart</button><button class="act" id="close">Schließen</button></div>
</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
const T=THREE,PRICE=4,KEY='holzfaeller-v1';
const $=id=>document.getElementById(id);
const fmt=n=>n.toLocaleString('de-DE');
const rnd=(a,b)=>a+Math.floor(Math.random()*(b-a+1)),rf=(a,b)=>a+Math.random()*(b-a);
let S={money:0,axe:1,cap:0,workers:0,carry:0,pile:0};
try{const s=JSON.parse(localStorage.getItem(KEY)||'null');if(s)S=Object.assign(S,s)}catch(e){}
const save=()=>{try{localStorage.setItem(KEY,JSON.stringify(S))}catch(e){}};
const cap=()=>3+2*S.cap;
const cost={axe:()=>Math.round(20*Math.pow(1.9,S.axe-1)),cap:()=>Math.round(15*Math.pow(1.7,S.cap)),worker:()=>Math.round(40*Math.pow(1.55,S.workers))};
const say=t=>{$('msg').textContent=t};
document.addEventListener('gesturestart',e=>e.preventDefault());

/* Renderer, Licht */
const dark=matchMedia('(prefers-color-scheme: dark)').matches;
const cv=$('c'),renderer=new T.WebGLRenderer({canvas:cv,antialias:true});
renderer.setPixelRatio(Math.min(devicePixelRatio||1,2));
renderer.outputEncoding=T.sRGBEncoding;renderer.toneMapping=T.ACESFilmicToneMapping;renderer.toneMappingExposure=dark?.8:.95;
renderer.shadowMap.enabled=true;renderer.shadowMap.type=T.PCFSoftShadowMap;
const scene=new T.Scene(),SKY=dark?0x131c26:0xa9cfe6;
scene.background=new T.Color(SKY);scene.fog=new T.Fog(SKY,32,70);
const cam=new T.PerspectiveCamera(50,1,.1,150);let CD=18;
function resize(){const w=innerWidth,h=innerHeight;renderer.setSize(w,h,false);cam.aspect=w/h;
  const hh=Math.atan(Math.tan(25*Math.PI/180)*cam.aspect);CD=Math.max(4.8/Math.tan(hh),14);cam.updateProjectionMatrix()}
addEventListener('resize',resize);addEventListener('orientationchange',resize);
scene.add(new T.HemisphereLight(0xdfeeff,0x3a4a2a,dark?.35:.6));
const sun=new T.DirectionalLight(0xfff0d6,dark?.5:1.15);sun.castShadow=true;sun.shadow.mapSize.set(2048,2048);sun.shadow.bias=-.0004;
Object.assign(sun.shadow.camera,{left:-17,right:17,top:17,bottom:-17,near:1,far:60});scene.add(sun,sun.target);

/* Texturen und Materialien */
function ctex(w,h,draw,rep){const c=document.createElement('canvas');c.width=w;c.height=h;draw(c.getContext('2d'),w,h);
  const t=new T.CanvasTexture(c);t.encoding=T.sRGBEncoding;t.anisotropy=4;if(rep){t.wrapS=t.wrapT=T.RepeatWrapping;t.repeat.set(rep[0],rep[1])}return t}
const M=o=>new T.MeshStandardMaterial(Object.assign({roughness:.92,metalness:0},o));
const grassT=ctex(256,256,(x,w,h)=>{x.fillStyle='#3f6e2e';x.fillRect(0,0,w,h);for(let i=0;i<2600;i++){x.fillStyle=`hsl(${rnd(85,110)},${rnd(35,55)}%,${rnd(20,36)}%)`;x.fillRect(rnd(0,w),rnd(0,h),rnd(1,3),rnd(1,4))}},[40,40]);
const barkT=ctex(128,128,(x,w,h)=>{x.fillStyle='#4e3322';x.fillRect(0,0,w,h);for(let i=0;i<90;i++){x.fillStyle=`rgba(${Math.random()<.5?'20,12,6':'120,85,55'},${rf(.15,.4)})`;x.fillRect(rnd(0,w),0,rnd(1,4),h)}},[2,1]);
const ringT=ctex(128,128,(x,w,h)=>{x.fillStyle='#d2ac74';x.fillRect(0,0,w,h);x.strokeStyle='#9c7440';x.lineWidth=2;for(let r=6;r<64;r+=6){x.beginPath();x.arc(64,64,r+rf(-1,1),0,7);x.stroke()}x.strokeStyle='#4e3322';x.lineWidth=5;x.beginPath();x.arc(64,64,62,0,7);x.stroke()});
const woodT=ctex(128,128,(x,w,h)=>{x.fillStyle='#9a6f40';x.fillRect(0,0,w,h);for(let y=0;y<h;y+=16){x.fillStyle='rgba(40,20,5,.45)';x.fillRect(0,y,w,2);for(let i=0;i<14;i++){x.fillStyle=`rgba(60,30,10,${rf(.05,.2)})`;x.fillRect(rnd(0,w),y+rnd(2,14),rnd(10,40),1)}}});
const plaidT=ctex(64,64,(x,w,h)=>{x.fillStyle='#a82828';x.fillRect(0,0,w,h);x.fillStyle='rgba(0,0,0,.5)';[0,32].forEach(p=>{x.fillRect(p,0,10,h);x.fillRect(0,p,w,10)});x.fillStyle='rgba(255,255,255,.18)';x.fillRect(18,0,3,h);x.fillRect(0,50,w,3)});
const awnT=ctex(64,8,(x,w,h)=>{for(let i=0;i<8;i++){x.fillStyle=i%2?'#f2ead8':'#b23a3a';x.fillRect(i*8,0,8,h)}});
const barkM=M({map:barkT}),woodM=M({map:woodT}),ringM=M({map:ringT}),awnM=M({map:awnT,side:T.DoubleSide});
const leafMs=[M({color:0x24592f,flatShading:true,side:T.DoubleSide}),M({color:0x2d6b38,flatShading:true,side:T.DoubleSide})];
const logMats=[barkM,ringM,ringM],stumpMats=[barkM,ringM,barkM];
const mesh=(g,m,x,y,z,par)=>{const o=new T.Mesh(g,m);o.position.set(x,y,z);o.castShadow=o.receiveShadow=true;if(par)par.add(o);return o};

/* Gelände */
const ground=new T.Mesh(new T.PlaneGeometry(200,200),M({map:grassT}));ground.rotation.x=-Math.PI/2;ground.receiveShadow=true;ground.userData={k:'ground'};scene.add(ground);
const STALL={x:-10,z:0},PILE={x:10,z:0};
[STALL,PILE].forEach(p=>{const d=new T.Mesh(new T.CircleGeometry(4.2,28),M({color:0x7d6040,roughness:1}));d.rotation.x=-Math.PI/2;d.position.set(p.x,.02,p.z);d.receiveShadow=true;scene.add(d)});
const LAYERS=[[1.3,1.6,1.75],[1.05,1.5,2.65],[.8,1.4,3.5],[.52,1.3,4.25]];
function jit(g,s){const p=g.attributes.position;for(let i=0;i<p.count;i++){const x=p.getX(i),y=p.getY(i),z=p.getZ(i);if(y<0){const a=Math.atan2(z,x),f=1+.16*Math.sin(a*3+s)+.1*Math.sin(a*7+s*2);p.setXYZ(i,x*f,y+.12*Math.sin(a*5+s),z*f)}}g.computeVertexNormals();return g}
const crowns=LAYERS.map(([r,h],i)=>jit(new T.ConeGeometry(r,h,10,1,true),i*1.7));
const trunkGeo=new T.CylinderGeometry(.2,.34,1.7,8);
/* Hintergrundwald (instanziert) */
{const N=60,pos=[];while(pos.length<N){const x=rf(-30,30),z=rf(-28,28);if(Math.abs(x)>17||Math.abs(z)>15)pos.push([x,z,rf(1.1,2),rf(0,6.3)])}
 const o=new T.Object3D(),set=(m,y)=>{pos.forEach(([x,z,s,r],i)=>{o.position.set(x,y*s,z);o.scale.setScalar(s);o.rotation.y=r;o.updateMatrix();m.setMatrixAt(i,o.matrix)});m.castShadow=true;scene.add(m)};
 set(new T.InstancedMesh(trunkGeo,barkM,N),.85);LAYERS.forEach(([,,y],k)=>set(new T.InstancedMesh(crowns[k],leafMs[k%2],N),y))}
/* Gras, Steine */
{const n=700,m=new T.InstancedMesh(new T.ConeGeometry(.07,.5,4),M({color:0xffffff}),n),o=new T.Object3D(),c=new T.Color();
 for(let i=0;i<n;i++){o.position.set(rf(-24,24),.2,rf(-22,22));o.rotation.set(rf(-.2,.2),rf(0,6),rf(-.2,.2));o.scale.setScalar(rf(.6,1.5));o.updateMatrix();m.setMatrixAt(i,o.matrix);c.setHSL(rf(.22,.31),rf(.4,.6),rf(.2,.35));m.setColorAt(i,c)}
 scene.add(m);
 for(let i=0;i<16;i++){const r=mesh(new T.DodecahedronGeometry(1,0),M({color:0x7b7b78,flatShading:true}),0,0,0);let x,z;do{x=rf(-22,22);z=rf(-20,20)}while(Math.abs(x)<8&&Math.abs(z)<7);const s=rf(.3,.9);r.position.set(x,s*.3,z);r.scale.set(s,s*.65,s*rf(.8,1.2));r.rotation.y=rf(0,6);scene.add(r)}}

/* Schilder */
function mkLabel(txt){const c=document.createElement('canvas');c.width=256;c.height=64;const t=new T.CanvasTexture(c);
  const sp=new T.Sprite(new T.SpriteMaterial({map:t,depthTest:false}));sp.scale.set(3,.75,1);sp.renderOrder=12;
  sp.set=s=>{const x=c.getContext('2d');x.clearRect(0,0,256,64);x.fillStyle='rgba(30,20,10,.65)';x.beginPath();x.roundRect?x.roundRect(4,6,248,52,14):x.rect(4,6,248,52);x.fill();x.fillStyle='#fff';x.font='bold 30px sans-serif';x.textAlign='center';x.textBaseline='middle';x.fillText(s,128,33);t.needsUpdate=true};sp.set(txt);return sp}

/* Menschen */
function mkPerson(o){
  const g=new T.Group(),sh=o.shirtMap?M({map:o.shirtMap}):M({color:o.shirt}),pa=M({color:o.pants}),sk=M({color:0xe0ac86}),bt=M({color:0x2e2218});
  const limb=(w,h,d,mat,x,y,hand)=>{const p=new T.Group();p.position.set(x,y,0);mesh(new T.BoxGeometry(w,h,d),mat,0,-h/2,0,p);if(hand)mesh(new T.BoxGeometry(.13,.12,.14),sk,0,-h-.03,0,p);else mesh(new T.BoxGeometry(w+.02,.16,d+.07),bt,0,-h+.08,.03,p);g.add(p);return p};
  const legL=limb(.2,.8,.24,pa,-.13,.8),legR=limb(.2,.8,.24,pa,.13,.8),armL=limb(.14,.6,.16,sh,-.34,1.38,1),armR=limb(.14,.6,.16,sh,.34,1.38,1);
  mesh(new T.BoxGeometry(.5,.6,.3),sh,0,1.1,0,g);
  mesh(new T.SphereGeometry(.17,12,10),sk,0,1.58,0,g);
  mesh(new T.SphereGeometry(.19,12,8,0,6.29,0,1.6),M({color:o.hat}),0,1.62,0,g);
  const ax=new T.Group();ax.position.set(0,-.62,.05);mesh(new T.CylinderGeometry(.028,.028,.85,6),woodM,0,0,.3,ax).rotation.x=Math.PI/2;
  mesh(new T.BoxGeometry(.05,.24,.16),M({color:0x9aa0a6,metalness:.6,roughness:.4}),0,0,.66,ax);armR.add(ax);
  g.userData.logs=[];
  return{g,legL,legR,armL,armR,ph:0,amp:0,chopP:null};
}
function animP(p,dt,mv){
  p.amp+=((mv?.75:0)-p.amp)*Math.min(1,dt*10);if(mv)p.ph+=dt*10;
  const s=Math.sin(p.ph)*p.amp;p.legL.rotation.x=s;p.legR.rotation.x=-s;p.armL.rotation.x=-s;
  p.armR.rotation.x=p.chopP!=null?-2.3+2*Math.pow(p.chopP,2.2):s*.8-.25;
  p.g.children[0]&&(p.g.position.y=Math.abs(Math.sin(p.ph))*.06*p.amp);
}

/* Marktstand mit Händler */
{const st=new T.Group();st.position.set(STALL.x,0,STALL.z);st.rotation.y=Math.PI/2;scene.add(st);
 mesh(new T.BoxGeometry(2.8,1,1.1),woodM,0,.5,.7,st);
 [-1.3,1.3].forEach(x=>[-.7,1.15].forEach(z=>mesh(new T.CylinderGeometry(.07,.07,2.5,6),barkM,x,1.25,z,st)));
 mesh(new T.BoxGeometry(3.3,.1,2.3),awnM,0,2.6,.25,st).rotation.x=.2;
 mesh(new T.BoxGeometry(2.8,1.9,.1),woodM,0,.95,-.7,st);
 [-.8,0,.8].forEach(x=>{const l=mesh(new T.CylinderGeometry(.14,.14,.7,8),logMats,x,1.1,.7,st);l.rotation.z=Math.PI/2});
 const m=mkPerson({shirt:0x3b6e8f,pants:0x4a3b2a,hat:0xd9a520});m.g.position.set(0,0,-.2);st.add(m.g);
 const l=mkLabel('Markt');l.position.set(STALL.x,4,STALL.z);scene.add(l)}
const PL=mkLabel('Lager 0');PL.position.set(PILE.x,3.4,PILE.z);scene.add(PL);
const logs=[];
[[5,.22],[4,.6],[3,.98],[2,1.36],[1,1.74]].forEach(([n,y])=>{for(let i=0;i<n;i++)[-.78,.78].forEach(dz=>{
  const l=mesh(new T.CylinderGeometry(.22,.22,1.45,9),logMats,PILE.x+(i-(n-1)/2)*.44,y,PILE.z+dz,scene);l.rotation.x=Math.PI/2;l.visible=false;logs.push(l)})});
const proxyM=new T.MeshBasicMaterial({transparent:true,opacity:0,depthWrite:false});
const sP=new T.Mesh(new T.BoxGeometry(3.4,3,3.6),proxyM);sP.position.set(STALL.x,1.5,STALL.z);sP.userData={k:'market'};
const pP=new T.Mesh(new T.BoxGeometry(3.6,2.4,3.4),proxyM);pP.position.set(PILE.x,1.2,PILE.z);pP.userData={k:'pile'};scene.add(sP,pP);

/* Bäume */
const tex=[null,1,2,3,4,5].map(n=>{if(!n)return null;const c=document.createElement('canvas');c.width=c.height=64;const x=c.getContext('2d');
  x.fillStyle='#6b4428';x.beginPath();x.arc(32,32,29,0,7);x.fill();x.lineWidth=4;x.strokeStyle='#f6f0e0';x.stroke();
  x.fillStyle='#fff';x.font='bold 38px sans-serif';x.textAlign='center';x.textBaseline='middle';x.fillText(n,32,35);return new T.CanvasTexture(c)});
const proxies=[],trees=[];
function mkTree(x,z,i){
  const g=new T.Group();g.position.set(x,0,z);g.rotation.y=rf(0,6);
  mesh(new T.CylinderGeometry(.3,.4,.35,9),stumpMats,0,.175,0,g);
  const top=new T.Group();top.position.y=.35;mesh(trunkGeo,barkM,0,.85,0,top);
  LAYERS.forEach(([,,y],k)=>mesh(crowns[k],leafMs[(i+k)%2],0,y,0,top).rotation.y=k*.9);g.add(top);
  const mk=(o,pr)=>{const s=new T.Sprite(new T.SpriteMaterial(o));s.renderOrder=10;g.add(s);return s};
  const lab=mk({depthTest:false});lab.scale.set(1.05,1.05,1);
  const bg=mk({color:0x000000,opacity:.55,transparent:true,depthTest:false});bg.scale.set(1.2,.16,1);
  const fg=mk({color:0x6fe08a,depthTest:false});fg.center.set(0,.5);fg.renderOrder=11;
  const px=new T.Mesh(new T.CylinderGeometry(1.3,1.3,4.6,8),proxyM);px.position.y=2.3;px.userData={k:'tree',i};g.add(px);proxies.push(px);
  scene.add(g);const t={x,z,g,top,lab,bg,fg,state:'alive',reserved:false,t:0,shake:0,dir:1,wait:0};
  reroll(t);show(t);return t}
function reroll(t){t.y=rnd(1,5);t.max=t.hp=t.y+2;t.s=.6+.1*t.y;t.top.scale.setScalar(t.s)}
function show(t){const y=.35+4.9*t.s+.6;t.lab.material.map=tex[t.y];t.lab.material.needsUpdate=true;t.lab.position.y=y;t.lab.visible=true;t.bg.position.set(0,y-.65,0);t.fg.position.set(-.6,y-.65,0);bar(t)}
function bar(t){const on=t.state==='alive'&&t.hp<t.max;t.bg.visible=t.fg.visible=on;t.fg.scale.set(Math.max(.001,1.2*t.hp/t.max),.12,1)}
function fell(t){t.state='falling';t.t=0;t.dir=Math.random()<.5?-1:1;t.lab.visible=t.bg.visible=t.fg.visible=false}
for(let r=0;r<4;r++)for(let c=0;c<3;c++)trees.push(mkTree((c-1)*3.8+rf(-.4,.4),(r-1.5)*3.8+rf(-.4,.4),r*3+c));
function updTree(t,dt){
  if(t.state==='alive'){if(t.shake>0){t.shake=Math.max(0,t.shake-dt);t.top.rotation.z=Math.sin(t.shake*50)*t.shake*.3}else t.top.rotation.z=0}
  else if(t.state==='falling'){t.t+=dt;const p=Math.min(1,t.t/.9);t.top.rotation.z=t.dir*p*p*1.5;t.top.scale.setScalar(t.s*(p<.7?1:1-(p-.7)/.3));if(p>=1){t.state='gone';t.top.visible=false;t.wait=3.5}}
  else if(t.state==='gone'){t.wait-=dt;if(t.wait<=0){reroll(t);t.top.scale.setScalar(.001);t.top.rotation.z=0;t.top.visible=true;t.state='growing';t.t=0}}
  else{t.t+=dt;const p=Math.min(1,t.t/.6);t.top.scale.setScalar(Math.max(.001,t.s*p));if(p>=1){t.state='alive';t.reserved=false;show(t)}}
}
function chop(t){
  if(t.state!=='alive')return;
  if(S.carry>=cap()){say('Dein Rucksack ist voll. Verkaufe dein Holz am Markt.');return}
  t.hp-=S.axe;t.shake=.3;
  if(t.hp<=0){const take=Math.min(t.y,cap()-S.carry),lost=t.y-take;S.carry+=take;fell(t);
    say(lost>0?`Baum gefällt: +${take} Holz. ${lost} passten nicht mehr in den Rucksack.`:`Baum gefällt: +${take} Holz.`)}
  bar(t);hud();save();
}

/* Spieler */
const P={x:-6,z:5,cd:0,sw:0,swT:null,p:mkPerson({shirtMap:plaidT,pants:0x2f3f5a,hat:0xc03030})};
scene.add(P.p.g);
const back=[];for(let i=0;i<6;i++){const l=mesh(new T.CylinderGeometry(.08,.08,.45,7),logMats,(i%2-.5)*.2,1.0+Math.floor(i/2)*.17,-.27,P.p.g);l.rotation.z=Math.PI/2;l.visible=false;back.push(l)}
let pending=null,target=null;const joy={x:0,y:0},keys={};
addEventListener('keydown',e=>keys[e.key.toLowerCase()]=1);addEventListener('keyup',e=>keys[e.key.toLowerCase()]=0);
const pend=()=>pending.k==='tree'?[pending.t.x,pending.t.z,2.1]:pending.k==='market'?[STALL.x,STALL.z,3.8]:[PILE.x,PILE.z,3.4];
function collect(){
  if(S.pile===0){say('Das Lager ist leer. Deine Mitarbeiter legen hier Holz ab.');return}
  if(S.carry>=cap()){say('Dein Rucksack ist voll. Verkaufe dein Holz am Markt.');return}
  const n=Math.min(S.pile,cap()-S.carry);S.pile-=n;S.carry+=n;say(`${n} Holz aus dem Lager genommen.`);hud();save()}
function updPlayer(dt){
  P.cd=Math.max(0,P.cd-dt);let ix=joy.x,iy=joy.y;
  if(keys.a||keys.arrowleft)ix-=1;if(keys.d||keys.arrowright)ix+=1;if(keys.w||keys.arrowup)iy-=1;if(keys.s||keys.arrowdown)iy+=1;
  const il=Math.hypot(ix,iy);let mx=0,mz=0;P.p.chopP=null;
  if(P.sw>0){P.sw-=dt;P.p.chopP=1-Math.max(0,P.sw)/.35;if(P.sw<=0){chop(P.swT)}}
  else if(il>.15){pending=null;target=null;const k=Math.min(1,il)/il;mx=ix*k;mz=iy*k}
  else if(pending||target){
    let px,pz,rg;if(pending)[px,pz,rg]=pend();else{px=target.x;pz=target.z;rg=.25}
    const dx=px-P.x,dz=pz-P.z,d=Math.hypot(dx,dz);
    if(d<=rg){
      if(!pending)target=null;
      else if(pending.k==='tree'){if(pending.t.state!=='alive')pending=null;else if(P.cd<=0){P.p.g.rotation.y=Math.atan2(dx,dz);P.sw=.35;P.cd=.5;P.swT=pending.t;pending=null}}
      else{P.p.g.rotation.y=Math.atan2(dx,dz);if(pending.k==='market'){$('sheet').classList.add('open');say('Willkommen am Markt.')}else collect();pending=null}
    }else{mx=dx/d;mz=dz/d}
  }
  const mv=mx||mz;
  if(mv){P.x+=mx*5*dt;P.z+=mz*5*dt;P.p.g.rotation.y=Math.atan2(mx,mz)}
  const bl=[{x:STALL.x,z:STALL.z,r:1.7},{x:PILE.x,z:PILE.z,r:1.6}];trees.forEach(t=>bl.push({x:t.x,z:t.z,r:t.state==='alive'?.85:.4}));
  bl.forEach(b=>{const dx=P.x-b.x,dz=P.z-b.z,d=Math.hypot(dx,dz),m=b.r+.35;if(d<m&&d>1e-4){P.x=b.x+dx/d*m;P.z=b.z+dz/d*m}});
  P.x=Math.max(-15,Math.min(15,P.x));P.z=Math.max(-13,Math.min(13,P.z));
  P.p.g.position.x=P.x;P.p.g.position.z=P.z;animP(P.p,dt,!!mv);
  if($('sheet').classList.contains('open')&&Math.hypot(P.x-STALL.x,P.z-STALL.z)>7)$('sheet').classList.remove('open');
}

/* Eingabe */
const ray=new T.Raycaster(),mv2=new T.Vector2();
cv.addEventListener('pointerdown',e=>{
  mv2.set(e.clientX/innerWidth*2-1,-(e.clientY/innerHeight)*2+1);ray.setFromCamera(mv2,cam);
  const h=ray.intersectObjects([...proxies,sP,pP,ground],false).find(x=>x.object.userData.k!=='tree'||trees[x.object.userData.i].state==='alive');
  if(!h)return;const u=h.object.userData;
  if(u.k==='tree')pending={k:'tree',t:trees[u.i]};
  else if(u.k==='ground'){pending=null;target={x:Math.max(-15,Math.min(15,h.point.x)),z:Math.max(-13,Math.min(13,h.point.z))}}
  else{pending={k:u.k};target=null}
});
const joyEl=$('joy'),knob=$('knob');let jid=null;
function jset(e){const r=joyEl.getBoundingClientRect(),m=r.width/2*.75;let dx=e.clientX-(r.left+r.width/2),dy=e.clientY-(r.top+r.height/2);const l=Math.hypot(dx,dy);if(l>m){dx*=m/l;dy*=m/l}knob.style.transform=`translate(${dx}px,${dy}px)`;joy.x=dx/m;joy.y=dy/m}
joyEl.addEventListener('pointerdown',e=>{jid=e.pointerId;joyEl.setPointerCapture(jid);jset(e)});
joyEl.addEventListener('pointermove',e=>{if(e.pointerId===jid)jset(e)});
const jend=e=>{if(e.pointerId===jid){jid=null;joy.x=joy.y=0;knob.style.transform=''}};
joyEl.addEventListener('pointerup',jend);joyEl.addEventListener('pointercancel',jend);

/* Mitarbeiter */
const workers=[],wcol=[[0x3a6ea5,0x6b4428],[0x2f8a6b,0x3b3b3b],[0x8a5fb0,0x4a3b2a],[0xc7a020,0x2f3f5a],[0xb5533a,0x3b3b3b]];
function mkWorker(){const c=wcol[workers.length%5],p=mkPerson({shirt:c[0],pants:c[1],hat:0xe0c040});
  const lg=mesh(new T.CylinderGeometry(.1,.1,.55,7),logMats,0,1.05,.36,p.g);lg.rotation.x=Math.PI/2;lg.visible=false;
  p.g.position.set(PILE.x-3-workers.length*.5,0,PILE.z+2);scene.add(p.g);return{p,lg,st:'idle',c:0,tm:0,tgt:null,mv:false}}
function go(w,x,z,dt){const g=w.p.g,dx=x-g.position.x,dz=z-g.position.z,d=Math.hypot(dx,dz);if(d<.12)return true;
  const m=Math.min(d,3*dt);g.position.x+=dx/d*m;g.position.z+=dz/d*m;g.rotation.y=Math.atan2(dx,dz);w.mv=true;return false}
function updWorker(w,dt){
  w.mv=false;w.p.chopP=null;
  if(w.st==='idle'){const c=trees.filter(t=>t.state==='alive'&&!t.reserved);if(c.length){w.tgt=c[rnd(0,c.length-1)];w.tgt.reserved=true;w.st='to'}}
  else if(w.st==='to'){if(w.tgt.state!=='alive'){w.st='idle'}else if(go(w,w.tgt.x,w.tgt.z+1.5,dt)){w.st='chop';w.tm=2.6;w.p.g.rotation.y=Math.PI}}
  else if(w.st==='chop'){if(w.tgt.state!=='alive'){w.st='idle'}else{w.tm-=dt;w.p.chopP=(performance.now()%650)/650;w.tgt.shake=.12;
    if(w.tm<=0){w.c=w.tgt.y;fell(w.tgt);w.lg.visible=true;w.st='back'}}}
  else if(w.st==='back'){if(go(w,PILE.x-2,PILE.z+.5,dt)){S.pile+=w.c;w.c=0;w.lg.visible=false;w.st='idle';hud();save()}}
  animP(w.p,dt,w.mv);
}

/* Oberfläche */
const items=[['axe','🪓','Bessere Axt'],['cap','🎒','Mehr Tragkraft'],['worker','🧑‍🌾','Mitarbeiter']];
$('shop').innerHTML=items.map(([k,ic,n])=>`<div class="item"><span class="ic">${ic}</span><div class="tx"><b>${n}</b><span id="d-${k}"></span></div><button class="act" data-k="${k}" id="b-${k}"></button></div>`).join('');
let lastPile=-1;
function hud(){
  while(workers.length<S.workers)workers.push(mkWorker());
  $('money').textContent=fmt(S.money)+' €';$('bag').textContent=S.carry+' / '+cap();$('bagBox').classList.toggle('full',S.carry>=cap());$('pile').textContent=fmt(S.pile);
  if(S.pile!==lastPile){lastPile=S.pile;PL.set('Lager '+S.pile);const n=S.pile>0?Math.min(logs.length,Math.ceil(S.pile/2)):0;logs.forEach((l,i)=>l.visible=i<n)}
  back.forEach((l,i)=>l.visible=i<S.carry);
  $('sell').disabled=S.carry===0;$('sell').textContent=S.carry?`Holz verkaufen (+${fmt(S.carry*PRICE)} €)`:'Kein Holz zum Verkaufen';
  $('d-axe').textContent=`Stufe ${S.axe}: ${S.axe} Schaden pro Hieb`;
  $('d-cap').textContent=`Trägt ${cap()}, danach ${cap()+2} Holz`;
  $('d-worker').textContent=`${S.workers} angestellt, jeder fällt Bäume für dich`;
  for(const k in cost){const c=cost[k]();$('b-'+k).textContent=fmt(c)+' €';$('b-'+k).disabled=S.money<c}
}
$('sell').onclick=()=>{const g=S.carry*PRICE;S.money+=g;say(`${S.carry} Holz verkauft für ${fmt(g)} €.`);S.carry=0;hud();save()};
$('close').onclick=()=>$('sheet').classList.remove('open');
$('shop').addEventListener('click',e=>{
  const b=e.target.closest('button[data-k]');if(!b||b.disabled)return;
  const k=b.dataset.k,c=cost[k]();if(S.money<c)return;S.money-=c;
  if(k==='axe'){S.axe++;say('Neue Axt gekauft. Du schlägst jetzt härter zu.')}
  if(k==='cap'){S.cap++;say(`Größerer Rucksack: Du trägst jetzt ${cap()} Holz.`)}
  if(k==='worker'){S.workers++;say('Ein neuer Mitarbeiter fällt jetzt Bäume für dich.')}
  hud();save();
});
$('reset').onclick=()=>{if(confirm('Spielstand wirklich löschen?')){S={money:0,axe:1,cap:0,workers:0,carry:0,pile:0};save();workers.forEach(w=>scene.remove(w.p.g));workers.length=0;hud();say('Neues Spiel gestartet.');$('sheet').classList.remove('open')}};

/* Schleife */
const clock=new T.Clock(),camT=new T.Vector3(P.x,0,P.z);
function loop(){requestAnimationFrame(loop);const dt=Math.min(clock.getDelta(),.1);
  trees.forEach(t=>updTree(t,dt));updPlayer(dt);workers.forEach(w=>updWorker(w,dt));
  camT.x+=(P.x-camT.x)*Math.min(1,dt*5);camT.z+=(P.z-camT.z)*Math.min(1,dt*5);
  cam.position.set(camT.x,CD*.78,camT.z+CD*.62);cam.lookAt(camT.x,0,camT.z-.5);
  sun.position.set(camT.x+9,18,camT.z+7);sun.target.position.set(camT.x,0,camT.z);sun.target.updateMatrixWorld();
  renderer.render(scene,cam)}
resize();hud();loop();
</script>
</body>
</html>
