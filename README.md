[个人网站index.html](https://github.com/user-attachments/files/25898885/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>李邦一 | 个人主页</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{font-family:-apple-system,'PingFang SC','Microsoft YaHei',sans-serif;background:#f0f2f5;color:#2d3436;line-height:1.8;}
nav{position:fixed;top:0;left:0;right:0;z-index:999;background:rgba(255,255,255,0.95);backdrop-filter:blur(10px);border-bottom:1px solid #e0e0e0;padding:0 30px;display:flex;justify-content:space-between;align-items:center;height:60px;}
nav .logo{font-size:20px;font-weight:700;color:#1a1a2e;}
nav .logo span{color:#0984e3;}
nav .nav-links a{margin-left:24px;font-size:14px;color:#636e72;text-decoration:none;font-weight:500;}
nav .nav-links a:hover{color:#0984e3;}
.hero{margin-top:60px;padding:70px 30px;text-align:center;background:linear-gradient(135deg,#0984e3,#6c5ce7);color:#fff;}
.hero h1{font-size:42px;margin-bottom:10px;}
.hero p{font-size:18px;opacity:0.9;margin-bottom:25px;}
.hero .btn{display:inline-block;padding:12px 32px;background:#fff;color:#0984e3;border-radius:30px;text-decoration:none;font-weight:600;margin:5px;}
.hero .btn:hover{background:#dfe6e9;}
section{max-width:900px;margin:50px auto;padding:0 20px;}
section h2{font-size:28px;margin-bottom:25px;text-align:center;color:#1a1a2e;}
.card{background:#fff;border-radius:14px;padding:28px;margin-bottom:20px;box-shadow:0 4px 15px rgba(0,0,0,0.06);position:relative;}
.card h3{font-size:18px;margin-bottom:8px;color:#0984e3;}
.card p{color:#636e72;font-size:14px;}
.card .edit-btn{position:absolute;top:15px;right:15px;background:#0984e3;color:#fff;border:none;padding:6px 14px;border-radius:8px;cursor:pointer;font-size:13px;}
.card .edit-btn:hover{background:#0770c2;}
.card .delete-btn{position:absolute;top:15px;right:80px;background:#d63031;color:#fff;border:none;padding:6px 14px;border-radius:8px;cursor:pointer;font-size:13px;}
.add-btn{display:block;width:100%;padding:16px;background:#dfe6e9;border:2px dashed #b2bec3;border-radius:14px;font-size:16px;color:#636e72;cursor:pointer;text-align:center;margin-bottom:20px;}
.add-btn:hover{background:#c8d6e5;color:#2d3436;}
.modal-overlay{display:none;position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,0.5);z-index:9999;justify-content:center;align-items:center;}
.modal-overlay.active{display:flex;}
.modal{background:#fff;border-radius:16px;padding:30px;width:90%;max-width:500px;max-height:80vh;overflow-y:auto;}
.modal h3{margin-bottom:18px;font-size:20px;}
.modal label{display:block;font-size:13px;font-weight:600;color:#636e72;margin-bottom:4px;margin-top:14px;}
.modal input,.modal textarea{width:100%;padding:10px 14px;border:1px solid #dfe6e9;border-radius:10px;font-size:14px;font-family:inherit;}
.modal textarea{height:100px;resize:vertical;}
.modal .modal-btns{display:flex;gap:10px;margin-top:22px;}
.modal .modal-btns button{flex:1;padding:12px;border:none;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;}
.modal .save-btn{background:#0984e3;color:#fff;}
.modal .cancel-btn{background:#dfe6e9;color:#2d3436;}
.resume-frame{width:100%;height:500px;border:1px solid #e0e0e0;border-radius:14px;background:#fff;}
footer{text-align:center;padding:30px;color:#b2bec3;font-size:13px;margin-top:40px;}
</style>
</head>
<body>

<nav>
  <div class="logo">李邦<span>一</span></div>
  <div class="nav-links">
    <a href="#resume">简历</a>
    <a href="#experience">经历</a>
    <a href="#portfolio">作品集</a>
  </div>
</nav>

<div class="hero">
  <h1>👋 你好，我是李邦一</h1>
  <p>欢迎来到我的个人主页</p>
  <a class="btn" href="#resume">查看简历</a>
  <a class="btn" href="#portfolio">浏览作品</a>
</div>

<!-- ====== 简历区域 ====== -->
<section id="resume">
  <h2>📄 我的简历</h2>
  <div class="card" style="text-align:center;">
    <p style="margin-bottom:15px;">点击下方按钮上传你的简历 PDF，将在此处展示</p>
    <input type="file" id="resumeUpload" accept=".pdf,.jpg,.png" style="margin-bottom:15px;">
    <div id="resumePreview"><p style="color:#b2bec3;">尚未上传简历</p></div>
  </div>
</section>

<!-- ====== 项目与实习经历 ====== -->
<section id="experience">
  <h2>💼 项目与实习经历</h2>
  <div id="expList"></div>
  <button class="add-btn" onclick="openExpModal(-1)">＋ 添加新经历</button>
</section>

<!-- ====== 作品集 ====== -->
<section id="portfolio">
  <h2>🎨 作品集</h2>
  <div id="pfList"></div>
  <button class="add-btn" onclick="openPfModal(-1)">＋ 添加新作品</button>
</section>

<footer>© 2026 李邦一 | 本页面内容可自由编辑</footer>

<!-- 经历编辑弹窗 -->
<div class="modal-overlay" id="expModal">
  <div class="modal">
    <h3 id="expModalTitle">添加经历</h3>
    <input type="hidden" id="expEditIdx">
    <label>公司/项目名称</label>
    <input type="text" id="expName" placeholder="如：字节跳动 / XX项目">
    <label>职位/角色</label>
    <input type="text" id="expRole" placeholder="如：前端实习生">
    <label>时间</label>
    <input type="text" id="expTime" placeholder="如：2025.06 - 2025.09">
    <label>描述</label>
    <textarea id="expDesc" placeholder="工作内容与收获..."></textarea>
    <div class="modal-btns">
      <button class="cancel-btn" onclick="closeExpModal()">取消</button>
      <button class="save-btn" onclick="saveExp()">保存</button>
    </div>
  </div>
</div>

<!-- 作品编辑弹窗 -->
<div class="modal-overlay" id="pfModal">
  <div class="modal">
    <h3 id="pfModalTitle">添加作品</h3>
    <input type="hidden" id="pfEditIdx">
    <label>作品名称</label>
    <input type="text" id="pfName" placeholder="如：个人博客系统">
    <label>作品描述</label>
    <textarea id="pfDesc" placeholder="简要描述作品内容..."></textarea>
    <label>链接（可选）</label>
    <input type="text" id="pfLink" placeholder="https://...">
    <div class="modal-btns">
      <button class="cancel-btn" onclick="closePfModal()">取消</button>
      <button class="save-btn" onclick="savePf()">保存</button>
    </div>
  </div>
</div>

<script>
/* ===== 简历上传 ===== */
document.getElementById('resumeUpload').addEventListener('change',function(e){
  var f=e.target.files[0];if(!f)return;
  var preview=document.getElementById('resumePreview');
  if(f.type==='application/pdf'){
    preview.innerHTML='<iframe src="'+URL.createObjectURL(f)+'" class="resume-frame"></iframe>';
  }else{
    preview.innerHTML='<img src="'+URL.createObjectURL(f)+'" style="max-width:100%;border-radius:14px;">';
  }
});

/* ===== 经历数据 ===== */
var exps=JSON.parse(localStorage.getItem('lby_exps')||'[]');
function renderExps(){
  var h='';
  for(var i=0;i<exps.length;i++){
    h+='<div class="card"><button class="delete-btn" onclick="delExp('+i+')">删除</button><button class="edit-btn" onclick="openExpModal('+i+')">编辑</button>';
    h+='<h3>'+exps[i].name+'</h3>';
    h+='<p><strong>'+exps[i].role+'</strong> &nbsp;|&nbsp; '+exps[i].time+'</p>';
    h+='<p style="margin-top:8px;">'+exps[i].desc+'</p></div>';
  }
  document.getElementById('expList').innerHTML=h;
  localStorage.setItem('lby_exps',JSON.stringify(exps));
}
function openExpModal(idx){
  document.getElementById('expEditIdx').value=idx;
  if(idx>=0){
    document.getElementById('expModalTitle').textContent='编辑经历';
    document.getElementById('expName').value=exps[idx].name;
    document.getElementById('expRole').value=exps[idx].role;
    document.getElementById('expTime').value=exps[idx].time;
    document.getElementById('expDesc').value=exps[idx].desc;
  }else{
    document.getElementById('expModalTitle').textContent='添加经历';
    document.getElementById('expName').value='';
    document.getElementById('expRole').value='';
    document.getElementById('expTime').value='';
    document.getElementById('expDesc').value='';
  }
  document.getElementById('expModal').classList.add('active');
}
function closeExpModal(){document.getElementById('expModal').classList.remove('active');}
function saveExp(){
  var idx=parseInt(document.getElementById('expEditIdx').value);
  var obj={name:document.getElementById('expName').value,role:document.getElementById('expRole').value,time:document.getElementById('expTime').value,desc:document.getElementById('expDesc').value};
  if(!obj.name){alert('请填写名称');return;}
  if(idx>=0){exps[idx]=obj;}else{exps.push(obj);}
  renderExps();closeExpModal();
}
function delExp(i){if(confirm('确认删除？')){exps.splice(i,1);renderExps();}}
renderExps();

/* ===== 作品数据 ===== */
var pfs=JSON.parse(localStorage.getItem('lby_pfs')||'[]');
function renderPfs(){
  var h='';
  for(var i=0;i<pfs.length;i++){
    h+='<div class="card"><button class="delete-btn" onclick="delPf('+i+')">删除</button><button class="edit-btn" onclick="openPfModal('+i+')">编辑</button>';
    h+='<h3>'+pfs[i].name+'</h3>';
    h+='<p>'+pfs[i].desc+'</p>';
    if(pfs[i].link){h+='<p style="margin-top:8px;"><a href="'+pfs[i].link+'" target="_blank">🔗 查看链接</a></p>';}
    h+='</div>';
  }
  document.getElementById('pfList').innerHTML=h;
  localStorage.setItem('lby_pfs',JSON.stringify(pfs));
}
function openPfModal(idx){
  document.getElementById('pfEditIdx').value=idx;
  if(idx>=0){
    document.getElementById('pfModalTitle').textContent='编辑作品';
    document.getElementById('pfName').value=pfs[idx].name;
    document.getElementById('pfDesc').value=pfs[idx].desc;
    document.getElementById('pfLink').value=pfs[idx].link||'';
  }else{
    document.getElementById('pfModalTitle').textContent='添加作品';
    document.getElementById('pfName').value='';
    document.getElementById('pfDesc').value='';
    document.getElementById('pfLink').value='';
  }
  document.getElementById('pfModal').classList.add('active');
}
function closePfModal(){document.getElementById('pfModal').classList.remove('active');}
function savePf(){
  var idx=parseInt(document.getElementById('pfEditIdx').value);
  var obj={name:document.getElementById('pfName').value,desc:document.getElementById('pfDesc').value,link:document.getElementById('pfLink').value};
  if(!obj.name){alert('请填写名称');return;}
  if(idx>=0){pfs[idx]=obj;}else{pfs.push(obj);}
  renderPfs();closePfModal();
}
function delPf(i){if(confirm('确认删除？')){pfs.splice(i,1);renderPfs();}}
renderPfs();

/* ===== 导航栏滚动阴影 ===== */
window.addEventListener('scroll',function(){
  var nav=document.querySelector('nav');
  if(window.scrollY>10){nav.style.boxShadow='0 2px 20px rgba(0,0,0,0.1)';}
  else{nav.style.boxShadow='none';}
});
</script>
</body>
</html>
