# CodingCamp-24Agustus26-ArshaAchdiSubono
repository coding camp 2026 arsha 

ini codingan saya (html css js) saya tidak bisa menaruh di file yg sesuai karna kendala di kiro yg tidak bisa memasukan codingan yg ada di file saya setelah saya commit


<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Focus Dashboard</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;font-family:Inter,Arial,sans-serif}body{min-height:100vh;background:linear-gradient(135deg,#111827,#312e81,#581c87);color:#fff;padding:35px}.container{max-width:1100px;margin:auto}.top{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);backdrop-filter:blur(15px);border-radius:25px;padding:30px 35px;margin-bottom:22px;display:flex;align-items:center;justify-content:space-between;box-shadow:0 15px 40px rgba(0,0,0,.2)}.brand h1{font-size:25px;margin-bottom:7px}.brand p{color:#cbd5e1;font-size:14px}.clock{text-align:right}.clock #time{font-size:38px;font-weight:700;letter-spacing:2px}.clock #date{font-size:13px;color:#cbd5e1;margin-top:4px}.grid{display:grid;grid-template-columns:1fr 1fr;gap:22px}.card{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.13);backdrop-filter:blur(15px);border-radius:22px;padding:25px;box-shadow:0 15px 35px rgba(0,0,0,.18)}.card h2{font-size:17px;margin-bottom:20px}.timer{text-align:center}.timer .circle{width:190px;height:190px;border-radius:50%;margin:10px auto 20px;border:8px solid rgba(255,255,255,.12);display:flex;align-items:center;justify-content:center;box-shadow:0 0 35px rgba(129,140,248,.25)}#timer{font-size:42px;font-weight:700}.buttons{display:flex;justify-content:center;gap:10px}.btn{border:0;border-radius:10px;padding:10px 18px;color:white;background:#6366f1;cursor:pointer;font-weight:600;transition:.2s}.btn:hover{transform:translateY(-2px);background:#818cf8}.btn.stop{background:#475569}.btn.reset{background:#7c3aed}.task-input{display:flex;gap:8px;margin-bottom:15px}.task-input input{flex:1;padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,.2);outline:none;background:rgba(0,0,0,.2);color:#fff}.task-input input::placeholder{color:#94a3b8}.task-list{list-style:none;display:flex;flex-direction:column;gap:9px}.task-list li{display:flex;align-items:center;justify-content:space-between;background:rgba(0,0,0,.18);padding:12px;border-radius:10px}.task-left{display:flex;align-items:center;gap:10px}.task-left input{width:17px;height:17px;accent-color:#818cf8}.task-left span.done{text-decoration:line-through;color:#94a3b8}.delete{border:0;background:#ef4444;color:white;border-radius:7px;padding:6px 10px;cursor:pointer}.links{grid-column:1/3}.link-form{display:flex;gap:10px;margin-bottom:17px}.link-form input{flex:1;padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,.2);background:rgba(0,0,0,.2);color:#fff;outline:none}.link-form input::placeholder{color:#94a3b8}.links-list{display:flex;gap:12px;flex-wrap:wrap}.link-item{display:flex;align-items:center;gap:5px}.link{display:block;text-decoration:none;color:#fff;background:linear-gradient(135deg,#6366f1,#8b5cf6);padding:11px 18px;border-radius:10px;font-size:14px;font-weight:600}.remove-link{border:0;background:#ef4444;color:#fff;border-radius:6px;padding:5px 7px;cursor:pointer}.quote{margin-top:22px;text-align:center;color:#cbd5e1;font-size:13px;font-style:italic}.progress{height:6px;background:rgba(255,255,255,.1);border-radius:10px;margin:0 auto 20px;max-width:300px;overflow:hidden}.progress-bar{height:100%;width:100%;background:linear-gradient(90deg,#818cf8,#c084fc);transition:width 1s linear}@media(max-width:750px){body{padding:15px}.top{flex-direction:column;gap:20px;text-align:center}.clock{text-align:center}.grid{grid-template-columns:1fr}.links{grid-column:auto}.link-form{flex-direction:column}.clock #time{font-size:30px}}
</style>
</head>
<body>

<div class="container">

<header class="top">
<div class="brand">
<h1>FocusSpace</h1>
<p id="greeting">Selamat pagi 👋</p>
</div>
<div class="clock">
<div id="time">00:00:00</div>
<div id="date">Loading...</div>
</div>
</header>
.
<main class="grid">

<section class="card timer">
<h2>⏱ Focus Session</h2>
<div class="circle">
<div id="timer">25:00</div>
</div>
<div class="progress"><div class="progress-bar" id="progress"></div></div>
<div class="buttons">
<button class="btn" onclick="startTimer()">Start</button>
<button class="btn stop" onclick="stopTimer()">Pause</button>
<button class="btn reset" onclick="resetTimer()">Reset</button>
</div>
<div class="quote">"Small progress is still progress."</div>
</section>

<section class="card">
<h2>✓ My Tasks</h2>
<div class="task-input">
<input id="taskInput" type="text" placeholder="Tambahkan tugas baru...">
<button class="btn" onclick="addTask()">Add</button>
</div>
<ul class="task-list" id="taskList"></ul>
</section>

<section class="card links">
<h2>⚡ Quick Access</h2>
<div class="link-form">
<input id="linkName" type="text" placeholder="Nama link">
<input id="linkURL" type="text" placeholder="https://example.com">
<button class="btn" onclick="addLink()">Add Link</button>
</div>
<div class="links-list" id="linksList"></div>
</section>

</main>
</div>

<script>
let seconds=25*60;
let timerInterval=null;
const timerDisplay=document.getElementById("timer");
const progress=document.getElementById("progress");

function updateClock(){
const now=new Date();
document.getElementById("time").textContent=now.toLocaleTimeString("id-ID");
document.getElementById("date").textContent=now.toLocaleDateString("id-ID",{weekday:"long",year:"numeric",month:"long",day:"numeric"});
let h=now.getHours();
let greeting=h<11?"Selamat pagi 👋":h<15?"Selamat siang ☀️":h<18?"Selamat sore 🌤️":"Selamat malam 🌙";
document.getElementById("greeting").textContent=greeting+" — siap fokus hari ini?";
}
setInterval(updateClock,1000);
updateClock();

function updateTimer(){
let min=Math.floor(seconds/60).toString().padStart(2,"0");
let sec=(seconds%60).toString().padStart(2,"0");
timerDisplay.textContent=min+":"+sec;
progress.style.width=(seconds/(25*60)*100)+"%";
if(seconds<=0){clearInterval(timerInterval);timerInterval=null;alert("Focus session selesai! 🎉");}
}
function startTimer(){
if(timerInterval)return;
timerInterval=setInterval(()=>{if(seconds>0){seconds--;updateTimer()}},1000);
}
function stopTimer(){
clearInterval(timerInterval);
timerInterval=null;
}
function resetTimer(){
stopTimer();
seconds=25*60;
updateTimer();
}
updateTimer();

let tasks=JSON.parse(localStorage.getItem("focusTasks")||"[]");

function saveTasks(){
localStorage.setItem("focusTasks",JSON.stringify(tasks));
}
function renderTasks(){
const list=document.getElementById("taskList");
list.innerHTML="";
tasks.forEach((task,index)=>{
const li=document.createElement("li");
li.innerHTML=`<div class="task-left"><input type="checkbox" ${task.done?"checked":""} onchange="toggleTask(${index})"><span class="${task.done?"done":""}">${escapeHTML(task.text)}</span></div><button class="delete" onclick="deleteTask(${index})">Delete</button>`;
list.appendChild(li);
});
}
function addTask(){
const input=document.getElementById("taskInput");
const text=input.value.trim();
if(!text)return;
tasks.push({text:text,done:false});
input.value="";
saveTasks();
renderTasks();
}
function toggleTask(index){
tasks[index].done=!tasks[index].done;
saveTasks();
renderTasks();
}
function deleteTask(index){
tasks.splice(index,1);
saveTasks();
renderTasks();
}
document.getElementById("taskInput").addEventListener("keydown",e=>{if(e.key==="Enter")addTask()});

function escapeHTML(text){
return text.replace(/[&<>"']/g,m=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;"}[m]));
}

let links=JSON.parse(localStorage.getItem("focusLinks")||'[{"name":"Google","url":"https://google.com"},{"name":"YouTube","url":"https://youtube.com"},{"name":"GitHub","url":"https://github.com"}]');

function saveLinks(){
localStorage.setItem("focusLinks",JSON.stringify(links));
}
function renderLinks(){
const container=document.getElementById("linksList");
container.innerHTML="";
links.forEach((link,index)=>{
const wrapper=document.createElement("div");
wrapper.className="link-item";
wrapper.innerHTML=`<a class="link" href="${link.url}" target="_blank">${escapeHTML(link.name)}</a><button class="remove-link" onclick="deleteLink(${index})">×</button>`;
container.appendChild(wrapper);
});
}
function addLink(){
const name=document.getElementById("linkName").value.trim();
let url=document.getElementById("linkURL").value.trim();
if(!name||!url)return;
if(!url.startsWith("http://")&&!url.startsWith("https://"))url="https://"+url;
links.push({name,url});
document.getElementById("linkName").value="";
document.getElementById("linkURL").value="";
saveLinks();
renderLinks();
}
function deleteLink(index){
links.splice(index,1);
saveLinks();
renderLinks();
}
renderTasks();
renderLinks();
</script>

</body>
</html>
