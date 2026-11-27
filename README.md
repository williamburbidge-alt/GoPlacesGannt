# GoPlacesGannt
group project Gannt chart and attendance 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Group project Gantt chart</title>
<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;600;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#f6f7f9;--card:#fff;--ink:#1c2430;--mute:#667085;--line:#e2e5ea;--s1:#2f7d6d;--s2:#c9811f;--s3:#4a5fc1;--s4:#b8466a;--today:#e5484d;--ok:#2f7d6d;--no:#b8466a;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#14181f;--card:#1d232d;--ink:#eef1f5;--mute:#98a2b3;--line:#303846;--s1:#4fb5a0;--s2:#e6a24a;--s3:#8196f0;--s4:#e4799b;--today:#ff6b70;--ok:#4fb5a0;--no:#e4799b}}
:root[data-theme="dark"]{--bg:#14181f;--card:#1d232d;--ink:#eef1f5;--mute:#98a2b3;--line:#303846;--s1:#4fb5a0;--s2:#e6a24a;--s3:#8196f0;--s4:#e4799b;--today:#ff6b70;--ok:#4fb5a0;--no:#e4799b}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:Figtree,system-ui,sans-serif;line-height:1.45}
main{max-width:900px;margin:0 auto;padding:20px 14px 48px}
h1{font-size:1.5rem;font-weight:800;margin:0 0 4px}
h2{font-size:1.1rem;font-weight:800;margin:28px 0 10px}
p.sub{margin:0;color:var(--mute);font-size:.9rem}
.card{background:var(--card);border:1px solid var(--line);border-radius:10px}
.scroll{overflow-x:auto;margin-top:14px}
.row{display:flex;align-items:stretch;border-bottom:1px solid var(--line);min-height:34px}
.row:last-child{border-bottom:0}
.lab{position:sticky;left:0;z-index:2;flex:0 0 130px;width:130px;background:var(--card);padding:7px 8px;font-size:.78rem;border-right:1px solid var(--line);display:flex;align-items:center}
.lab.sec{font-weight:800;font-size:.82rem;gap:6px}
.dot{width:9px;height:9px;border-radius:50%;flex:none}
.track{position:relative;flex:none;background-image:repeating-linear-gradient(90deg,transparent 0 21px,var(--line) 21px 22px)}
.track.wk{background-image:repeating-linear-gradient(90deg,transparent 0 153px,var(--line) 153px 154px)}
.hd .track{font-size:.68rem;color:var(--mute)}
.hd span{position:absolute;top:8px;white-space:nowrap}
.bar{position:absolute;top:7px;height:20px;border-radius:5px;color:#fff;font-size:.68rem;font-weight:600;padding:2px 6px;white-space:nowrap;overflow:hidden}
.bar.done{opacity:.55}
.today{position:absolute;top:0;bottom:0;width:2px;background:var(--today);z-index:1}
.dia{position:absolute;top:9px;width:16px;height:16px;transform:rotate(45deg);background:var(--s3);border-radius:3px}
.legend{display:flex;gap:14px;flex-wrap:wrap;font-size:.75rem;color:var(--mute);margin-top:8px}
.legend i{display:inline-block;vertical-align:middle;margin-right:4px}
.tasks{padding:4px 12px}
.t{display:grid;grid-template-columns:1fr auto auto;gap:8px;align-items:center;padding:9px 0;border-bottom:1px solid var(--line);font-size:.85rem}
.t:last-child{border-bottom:0}
.t b{font-weight:600}.t small{display:block;color:var(--mute)}
input,button{font:inherit;color:var(--ink)}
input[type=date],input[type=text]{background:var(--bg);border:1px solid var(--line);border-radius:6px;padding:6px 8px;font-size:.8rem;max-width:100%}
.m{padding:12px;margin-bottom:10px}
.mh{display:flex;justify-content:space-between;gap:8px;align-items:baseline}
.mh b{font-weight:800}.mh span{color:var(--mute);font-size:.8rem}
.chips{display:flex;flex-wrap:wrap;gap:6px;margin:10px 0 6px}
.chip{border:1.5px solid var(--line);background:var(--bg);border-radius:20px;padding:6px 12px;font-size:.82rem;cursor:pointer;min-height:36px}
.chip.p{background:var(--ok);border-color:var(--ok);color:#fff}
.chip.a{background:transparent;border-color:var(--no);color:var(--no);text-decoration:line-through}
.cnt{font-size:.78rem;color:var(--mute)}
.x{background:none;border:0;color:var(--mute);cursor:pointer;font-size:.78rem;text-decoration:underline;padding:0}
.add{display:flex;flex-wrap:wrap;gap:8px;padding:12px;align-items:center}
.add input[type=text]{flex:1 1 140px}
.btn{background:var(--s3);color:#fff;border:0;border-radius:6px;padding:8px 14px;font-weight:600;cursor:pointer}
.tot{width:100%;border-collapse:collapse;font-size:.82rem}
.tot td{padding:6px 12px;border-bottom:1px solid var(--line)}
.tot tr:last-child td{border-bottom:0}.tot td:last-child{text-align:right;color:var(--mute)}
</style>
</head>
<body>
<main>
<h1>Group project Gantt chart</h1>
<p class="sub">Tap a member under a meeting to mark them present, tap again for absent, and again to clear.</p>

<div class="card scroll"><div id="g"></div></div>
<div class="legend"><span><i class="dot" style="background:var(--today);width:12px;height:3px;border-radius:0"></i>Today</span><span><i class="dot" style="background:var(--s3);border-radius:2px;transform:rotate(45deg);width:8px;height:8px"></i>Meeting</span><span>Faded bars are finished</span></div>

<h2>Tasks and dates</h2>
<div class="card tasks" id="tasks"></div>

<h2>Meeting attendance</h2>
<div id="meets"></div>
<div class="card add">
<input type="date" id="nd"><input type="text" id="nt" placeholder="Meeting name" maxlength="60">
<button class="btn" id="addm">Add meeting</button>
</div>

<h2>Attendance totals</h2>
<div class="card"><table class="tot" id="tot"></table></div>
</main>

<script>
var MEMBERS=["William","Zaya","Jiahao","Bowen","Luke","James"];
var START=Date.UTC(2026,10,12),DAYS=73,W=22,LAB=130;
var COL=["var(--s1)","var(--s2)","var(--s3)","var(--s4)"];
var SECS=["Meetings and role selection","Research","Scripts and PowerPoint","Presentation practice"];
var def={
tasks:[
{id:"t1",sec:0,name:"Meet, plan and pick roles",s:"2026-11-12",e:"2026-11-25"},
{id:"t2",sec:0,name:"Project proposal (Luke)",s:"2026-11-20",e:"2026-11-24"},
{id:"t3",sec:0,name:"Lecturer meeting with Kevan",s:"2026-12-01",e:"2026-12-01"},
{id:"t4",sec:1,name:"Research",s:"2026-12-02",e:"2026-12-20"},
{id:"t5",sec:2,name:"Write scripts",s:"2026-12-21",e:"2027-01-10"},
{id:"t6",sec:2,name:"Build the PowerPoint",s:"2026-12-28",e:"2027-01-14"},
{id:"t7",sec:3,name:"Practice the presentation",s:"2027-01-15",e:"2027-01-21"},
{id:"t8",sec:3,name:"Present (deadline)",s:"2027-01-22",e:"2027-01-22"}],
meetings:[
{id:"m1",date:"2026-11-12",title:"Introductions and planning"},
{id:"m2",date:"2026-11-20",title:"Project proposal discussion"},
{id:"m3",date:"2026-11-25",title:"Group meeting"},
{id:"m4",date:"2026-12-01",title:"Meeting with Kevan"}],
att:{}};
var S;
try{S=JSON.parse(localStorage.getItem("gp-gantt-v2"))}catch(e){S=null}
if(!S||!S.tasks)S=def;
function save(){try{localStorage.setItem("gp-gantt-v2",JSON.stringify(S))}catch(e){}}
function idx(s){return Math.round((Date.parse(s+"T00:00:00Z")-START)/864e5)}
function fmt(s){var d=new Date(Date.parse(s+"T00:00:00Z"));return d.toLocaleDateString("en-GB",{day:"numeric",month:"short",timeZone:"UTC"})}
function todayStr(){var n=new Date();return n.getFullYear()+"-"+String(n.getMonth()+1).padStart(2,"0")+"-"+String(n.getDate()).padStart(2,"0")}
function esc(t){return String(t).replace(/[&<>"]/g,function(c){return{"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]})}

function gantt(){
var tw=DAYS*W,td=idx(todayStr()),h="";
var tl=td>=0&&td<DAYS?'<div class="today" style="left:'+(td*W+W/2-1)+'px"></div>':"";
var hd="";
for(var i=0;i<DAYS;i+=7){var d=new Date(START+i*864e5);hd+='<span style="left:'+(i*W+4)+'px">'+d.toLocaleDateString("en-GB",{day:"numeric",month:"short",timeZone:"UTC"})+'</span>'}
h+='<div class="row hd" style="width:'+(tw+LAB)+'px"><div class="lab"></div><div class="track wk" style="width:'+tw+'px;height:30px">'+hd+'</div></div>';
for(var s=0;s<4;s++){
h+='<div class="row" style="width:'+(tw+LAB)+'px"><div class="lab sec"><i class="dot" style="background:'+COL[s]+'"></i>'+SECS[s]+'</div><div class="track" style="width:'+tw+'px">'+tl+'</div></div>';
S.tasks.filter(function(t){return t.sec===s}).forEach(function(t){
var a=idx(t.s),b=idx(t.e);if(b<a)b=a;
var done=b<td;
h+='<div class="row" style="width:'+(tw+LAB)+'px"><div class="lab">'+esc(t.name)+'</div><div class="track" style="width:'+tw+'px">'+tl+'<div class="bar'+(done?" done":"")+'" style="left:'+(a*W)+'px;width:'+((b-a+1)*W-2)+'px;background:'+COL[s]+'">'+(b-a>3?esc(t.name):"")+'</div></div></div>'});
if(s===0){
var dm="";S.meetings.forEach(function(m){var i=idx(m.date);if(i>=0&&i<DAYS)dm+='<div class="dia" title="'+esc(m.title)+'" style="left:'+(i*W+3)+'px"></div>'});
h+='<div class="row" style="width:'+(tw+LAB)+'px"><div class="lab">Meetings</div><div class="track" style="width:'+tw+'px">'+tl+dm+'</div></div>'}
}
document.getElementById("g").innerHTML=h}

function tasks(){
var h="";S.tasks.forEach(function(t){
h+='<div class="t"><div><b>'+esc(t.name)+'</b><small>'+SECS[t.sec]+'</small></div><label><small>Start</small><input type="date" value="'+t.s+'" data-id="'+t.id+'" data-f="s"></label><label><small>End</small><input type="date" value="'+t.e+'" data-id="'+t.id+'" data-f="e"></label></div>'});
document.getElementById("tasks").innerHTML=h}

function meets(){
var h="";
S.meetings.slice().sort(function(a,b){return a.date<b.date?-1:1}).forEach(function(m){
var a=S.att[m.id]||{},p=0,n=0;
var chips=MEMBERS.map(function(x){var v=a[x];if(v==="p")p++;if(v==="a")n++;
return '<button class="chip '+(v||"")+'" data-m="'+m.id+'" data-p="'+x+'">'+x+'</button>'}).join("");
h+='<div class="card m"><div class="mh"><b>'+esc(m.title)+'</b><span>'+fmt(m.date)+'</span></div><div class="chips">'+chips+'</div><div class="cnt">'+p+' present, '+n+' absent, '+(MEMBERS.length-p-n)+' not marked &nbsp; <button class="x" data-del="'+m.id+'">Remove meeting</button></div></div>'});
document.getElementById("meets").innerHTML=h;
var t='<tr><td><b>Member</b></td><td><b>Present</b></td></tr>';
MEMBERS.forEach(function(x){var c=0;S.meetings.forEach(function(m){if((S.att[m.id]||{})[x]==="p")c++});
t+='<tr><td>'+x+'</td><td>'+c+' of '+S.meetings.length+' meetings</td></tr>'});
document.getElementById("tot").innerHTML=t}

function all(){gantt();meets()}
document.addEventListener("click",function(e){
var c=e.target.closest(".chip");
if(c){var m=c.dataset.m,p=c.dataset.p;S.att[m]=S.att[m]||{};var v=S.att[m][p];
if(!v)S.att[m][p]="p";else if(v==="p")S.att[m][p]="a";else delete S.att[m][p];
save();meets();return}
var d=e.target.closest("[data-del]");
if(d&&confirm("Remove this meeting and its attendance?")){S.meetings=S.meetings.filter(function(m){return m.id!==d.dataset.del});delete S.att[d.dataset.del];save();all()}});
document.getElementById("tasks").addEventListener("change",function(e){
var i=e.target;if(!i.dataset.id||!i.value)return;
S.tasks.forEach(function(t){if(t.id===i.dataset.id)t[i.dataset.f]=i.value});save();gantt()});
document.getElementById("addm").addEventListener("click",function(){
var d=document.getElementById("nd").value,t=document.getElementById("nt").value.trim();
if(!d){document.getElementById("nd").focus();return}
S.meetings.push({id:"m"+Date.now(),date:d,title:t||"Group meeting"});
document.getElementById("nt").value="";save();all()});
document.getElementById("nd").value=todayStr();
tasks();all();
</script>
</body>
</html>
