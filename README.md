# gzh-try
[index.html](https://github.com/user-attachments/files/34372552/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>我的作品集 · 照片与笔记</title>
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Crect width='32' height='32' rx='7' fill='%232E4B3C'/%3E%3Ccircle cx='16' cy='13' r='6' fill='none' stroke='%23F5F2EB' stroke-width='2'/%3E%3Cpath d='M6 26c2-5 6-7 10-7s8 2 10 7' fill='none' stroke='%23A86A3D' stroke-width='2' stroke-linecap='round'/%3E%3C/svg%3E">
<style>
  /* ===== 设计变量 ===== */
  :root{
    --paper:#F5F2EB;        /* 纸感暖白 */
    --card:#FCFBF7;         /* 卡片白 */
    --ink:#20271F;          /* 墨色文字 */
    --green:#2E4B3C;        /* 主色墨绿 */
    --green-deep:#1E352B;
    --ochre:#A86A3D;        /* 赭石点缀 */
    --muted:#6B7168;        /* 次要文字 */
    --line:#E0DBD0;         /* 细线 */
    --serif:'Noto Serif SC','Source Han Serif SC','Songti SC','STSong','SimSun',serif;
    --sans:'PingFang SC','Hiragino Sans GB','Microsoft YaHei','Noto Sans SC',sans-serif;
  }
  *{margin:0;padding:0;box-sizing:border-box}
  html{scroll-behavior:smooth}
  body{
    font-family:var(--sans);
    background:var(--paper);
    color:var(--ink);
    line-height:1.75;
    -webkit-font-smoothing:antialiased;
  }
  img{display:block;max-width:100%}
  a{color:inherit;text-decoration:none}
  .wrap{width:min(1120px,92%);margin:0 auto}

  /* ===== 顶部导航 ===== */
  header.nav{
    position:sticky;top:0;z-index:50;
    background:rgba(245,242,235,.92);
    border-bottom:1px solid var(--line);
  }
  .nav-inner{display:flex;align-items:center;justify-content:space-between;height:66px}
  .brand{font-family:var(--serif);font-size:21px;font-weight:700;letter-spacing:.5px}
  .brand span{color:var(--ochre)}
  .nav-links{display:flex;gap:34px;list-style:none}
  .nav-links a{
    font-size:15px;color:var(--muted);position:relative;padding:6px 0;
    transition:color .2s;
  }
  .nav-links a:hover{color:var(--green)}
  .nav-links a::after{
    content:"";position:absolute;left:0;bottom:0;height:2px;width:0;
    background:var(--ochre);transition:width .25s;
  }
  .nav-links a:hover::after{width:100%}
  .menu-btn{
    display:none;background:none;border:1px solid var(--line);border-radius:8px;
    width:42px;height:42px;cursor:pointer;align-items:center;justify-content:center;
  }
  .menu-btn svg{width:22px;height:22px;stroke:var(--ink)}

  /* ===== Hero 刊头 ===== */
  .hero{padding:64px 0 56px}
  .hero-grid{display:grid;grid-template-columns:1.05fr .95fr;gap:48px;align-items:center}
  .hero-eyebrow{
    font-family:var(--serif);color:var(--ochre);font-size:15px;letter-spacing:2px;margin-bottom:18px;
  }
  .hero h1{
    font-family:var(--serif);font-weight:700;
    font-size:clamp(34px,5vw,56px);line-height:1.22;margin-bottom:22px;
  }
  .hero p{color:var(--muted);font-size:16.5px;max-width:460px;margin-bottom:32px}
  .hero-actions{display:flex;gap:16px;flex-wrap:wrap}
  .btn{
    display:inline-flex;align-items:center;gap:9px;
    padding:13px 26px;border-radius:10px;font-size:15px;cursor:pointer;
    border:1px solid var(--green);transition:all .2s;
  }
  .btn-primary{background:var(--green);color:#fff}
  .btn-primary:hover{background:var(--green-deep)}
  .btn-ghost{background:transparent;color:var(--green)}
  .btn-ghost:hover{background:var(--green);color:#fff}
  .hero-photo{position:relative}
  .hero-photo img{
    width:100%;height:460px;object-fit:cover;border-radius:14px;
    box-shadow:0 22px 50px -22px rgba(30,53,43,.55);
  }
  .hero-photo figcaption{
    position:absolute;left:18px;bottom:16px;color:#fff;font-size:13.5px;
    background:rgba(30,53,43,.62);padding:6px 14px;border-radius:20px;backdrop-filter:blur(4px);
  }

  /* ===== 通用区块 ===== */
  section.block{padding:62px 0}
  .sec-head{margin-bottom:38px;max-width:640px}
  .sec-head h2{
    font-family:var(--serif);font-size:clamp(27px,3.4vw,38px);font-weight:700;margin-bottom:12px;
  }
  .sec-head p{color:var(--muted);font-size:15.5px}
  .sec-rule{width:54px;height:3px;background:var(--ochre);border:none;margin-bottom:20px}

  /* ===== 相册瀑布流 ===== */
  .gallery{column-count:3;column-gap:22px}
  .photo-card{
    break-inside:avoid;margin-bottom:22px;background:var(--card);
    border:1px solid var(--line);border-radius:12px;overflow:hidden;cursor:pointer;
    transition:transform .25s,box-shadow .25s;
  }
  .photo-card:hover{transform:translateY(-5px);box-shadow:0 18px 34px -20px rgba(30,53,43,.5)}
  .photo-card img{width:100%;object-fit:cover}
  .photo-meta{padding:13px 16px}
  .photo-meta h3{font-family:var(--serif);font-size:16px;font-weight:600}
  .photo-meta p{font-size:13px;color:var(--muted);margin-top:2px}

  /* ===== Lightbox ===== */
  .lightbox{
    position:fixed;inset:0;z-index:100;background:rgba(20,26,21,.9);
    display:none;align-items:center;justify-content:center;padding:30px;
  }
  .lightbox.open{display:flex}
  .lightbox img{max-width:90%;max-height:82vh;border-radius:10px;object-fit:contain}
  .lightbox-cap{position:absolute;bottom:26px;left:0;right:0;text-align:center;color:#e8e4da;font-size:14px}
  .lb-btn{
    position:absolute;background:rgba(255,255,255,.12);border:none;color:#fff;
    width:48px;height:48px;border-radius:50%;font-size:22px;cursor:pointer;
    display:flex;align-items:center;justify-content:center;transition:background .2s;
  }
  .lb-btn:hover{background:rgba(255,255,255,.28)}
  .lb-close{top:24px;right:26px}
  .lb-prev{left:26px;top:50%;transform:translateY(-50%)}
  .lb-next{right:26px;top:50%;transform:translateY(-50%)}

  /* ===== 笔记 ===== */
  .notes{display:grid;grid-template-columns:repeat(2,1fr);gap:22px}
  .note-card{
    background:var(--card);border:1px solid var(--line);border-radius:12px;
    padding:26px 28px;display:flex;flex-direction:column;
  }
  .note-date{font-size:13px;color:var(--ochre);letter-spacing:1px;margin-bottom:10px}
  .note-card h3{font-family:var(--serif);font-size:20px;font-weight:700;margin-bottom:10px}
  .note-summary{color:var(--muted);font-size:15px}
  .note-full{
    color:var(--ink);font-size:15px;margin-top:14px;padding-top:14px;
    border-top:1px dashed var(--line);display:none;
  }
  .note-card.expanded .note-full{display:block}
  .note-tags{display:flex;gap:8px;flex-wrap:wrap;margin-top:16px}
  .tag{
    font-size:12.5px;color:var(--green);background:rgba(46,75,60,.08);
    padding:3px 12px;border-radius:14px;
  }
  .note-toggle{
    margin-top:18px;align-self:flex-start;background:none;border:none;
    color:var(--green);font-size:14px;cursor:pointer;padding:6px 0;
    border-bottom:1px solid transparent;
  }
  .note-toggle:hover{border-bottom-color:var(--ochre)}

  /* ===== 关于 ===== */
  .about{
    background:var(--green-deep);color:#E9E5DA;border-radius:16px;
    padding:52px 50px;display:grid;grid-template-columns:160px 1fr;gap:40px;align-items:center;
  }
  .about-avatar{
    width:160px;height:160px;border-radius:50%;object-fit:cover;
    border:3px solid rgba(255,255,255,.25);
  }
  .about h2{font-family:var(--serif);font-size:28px;margin-bottom:14px;color:#fff}
  .about p{font-size:15.5px;color:#C9CFC6;margin-bottom:14px}
  .about-links{display:flex;gap:22px;flex-wrap:wrap;margin-top:18px}
  .about-links a{font-size:14.5px;color:#E7C9A8;border-bottom:1px solid rgba(231,201,168,.4);padding-bottom:2px}
  .about-links a:hover{color:#fff}

  /* ===== 页脚 ===== */
  footer{border-top:1px solid var(--line);padding:30px 0;margin-top:30px}
  .foot-inner{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px}
  footer p{font-size:13.5px;color:var(--muted)}

  /* ===== 响应式 ===== */
  @media (max-width:900px){
    .hero-grid{grid-template-columns:1fr;gap:34px}
    .hero-photo img{height:340px}
    .gallery{column-count:2}
    .about{grid-template-columns:1fr;padding:40px 30px;text-align:center}
    .about-avatar{margin:0 auto}
    .about-links{justify-content:center}
  }
  @media (max-width:600px){
    .nav-links{
      display:none;position:absolute;top:66px;left:0;right:0;
      background:var(--paper);flex-direction:column;gap:0;
      border-bottom:1px solid var(--line);padding:8px 0;
    }
    .nav-links.open{display:flex}
    .nav-links li{width:100%}
    .nav-links a{display:block;padding:14px 6%}
    .nav-links a::after{display:none}
    .menu-btn{display:flex}
    .gallery{column-count:1}
    .notes{grid-template-columns:1fr}
    .hero{padding:40px 0}
    section.block{padding:44px 0}
    .lb-prev{left:10px}.lb-next{right:10px}
  }
</style>
</head>
<body>

<!-- ===== 导航 ===== -->
<header class="nav">
  <div class="wrap nav-inner">
    <div class="brand">我的作品集<span>。</span></div>
    <ul class="nav-links" id="navLinks">
      <li><a href="#gallery">相册</a></li>
      <li><a href="#notes">笔记</a></li>
      <li><a href="#about">关于</a></li>
    </ul>
    <button class="menu-btn" id="menuBtn" aria-label="菜单">
      <svg viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round"><path d="M4 7h16M4 12h16M4 17h16"/></svg>
    </button>
  </div>
</header>

<!-- ===== Hero ===== -->
<div class="wrap hero">
  <div class="hero-grid">
    <div>
      <div class="hero-eyebrow">PHOTO &amp; JOURNAL</div>
      <h1>把走过的风景<br>和写下的思考，都收在这里</h1>
      <p>这是我的个人作品集，用来存放摄影照片与学习笔记。慢慢更新，记录生活，也记录成长。</p>
      <div class="hero-actions">
        <a class="btn btn-primary" href="#gallery">浏览相册</a>
        <a class="btn btn-ghost" href="#notes">阅读笔记</a>
      </div>
    </div>
    <figure class="hero-photo">
      <img src="https://picsum.photos/seed/cover-main/820/920" alt="封面照片">
      <figcaption>示例封面 · 替换成你最喜欢的一张</figcaption>
    </figure>
  </div>
</div>

<!-- ===== 相册 ===== -->
<section class="block" id="gallery">
  <div class="wrap">
    <div class="sec-head">
      <hr class="sec-rule">
      <h2>相册</h2>
      <p>点击任意照片可以放大查看。下面是示例照片，换成你自己的作品即可。</p>
    </div>
    <div class="gallery" id="galleryBox"></div>
  </div>
</section>

<!-- ===== 笔记 ===== -->
<section class="block" id="notes">
  <div class="wrap">
    <div class="sec-head">
      <hr class="sec-rule">
      <h2>笔记</h2>
      <p>学习心得、技术笔记和生活记录。点击「展开阅读」查看完整内容。</p>
    </div>
    <div class="notes" id="notesBox"></div>
  </div>
</section>

<!-- ===== 关于 ===== -->
<section class="block" id="about">
  <div class="wrap">
    <div class="about">
      <img class="about-avatar" src="https://picsum.photos/seed/avatar-me/300/300" alt="头像">
      <div>
        <h2>关于我</h2>
        <p>你好，我是一名网络工程专业的学生，喜欢摄影，也喜欢把学到的东西整理成笔记。这里是我的小角落，欢迎随便逛逛。</p>
        <p>（这段自我介绍、头像和下面的联系方式都可以替换成你自己的。）</p>
        <div class="about-links">
          <a href="mailto:your@email.com">邮箱：your@email.com</a>
          <a href="https://github.com/你的用户名" target="_blank" rel="noopener">GitHub</a>
          <a href="#gallery">回到相册</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== 页脚 ===== -->
<footer>
  <div class="wrap foot-inner">
    <p>© 2026 我的作品集 · 保留所有权利</p>
    <p>由 GitHub Pages 免费托管</p>
  </div>
</footer>

<!-- ===== Lightbox ===== -->
<div class="lightbox" id="lightbox">
  <button class="lb-btn lb-close" id="lbClose" aria-label="关闭">×</button>
  <button class="lb-btn lb-prev" id="lbPrev" aria-label="上一张">‹</button>
  <img id="lbImg" src="" alt="">
  <button class="lb-btn lb-next" id="lbNext" aria-label="下一张">›</button>
  <div class="lightbox-cap" id="lbCap"></div>
</div>

<script>
/* =========================================================
   数据区：以后你只需要改这里，就能增删照片和笔记
   照片路径可换成本地文件，如 "assets/photo1.jpg"
   ========================================================= */
const PHOTOS = [
  {src:"https://picsum.photos/seed/city-dusk/600/780",  title:"城市黄昏", place:"广州 · 天台"},
  {src:"https://picsum.photos/seed/old-street/600/450", title:"老街巷",   place:"佛山 · 老城区"},
  {src:"https://picsum.photos/seed/night-view/600/820", title:"夜色",     place:"珠江边"},
  {src:"https://picsum.photos/seed/campus-life/600/600",title:"校园一角", place:"学校"},
  {src:"https://picsum.photos/seed/green-hill/600/760", title:"山间",     place:"周末徒步"},
  {src:"https://picsum.photos/seed/coffee-time/600/480",title:"一杯咖啡", place:"午后"},
  {src:"https://picsum.photos/seed/building-line/600/800",title:"建筑线条",place:"城市"},
  {src:"https://picsum.photos/seed/sea-wind/600/520",   title:"海风",     place:"海边"},
  {src:"https://picsum.photos/seed/quiet-road/600/700", title:"安静的路", place:"傍晚"}
];

const NOTES = [
  {
    date:"2026 · 10 · 29",
    title:"VLAN 到底解决了什么问题",
    summary:"用最直白的话，理解为什么要把一个物理交换机逻辑上切成几块。",
    tags:["网络工程","VLAN","学习笔记"],
    full:"VLAN（虚拟局域网）的核心作用是广播隔离和灵活分组。同一个 VLAN 里的设备像在同一个交换机下，能直接二层互通；不同 VLAN 之间默认隔离，需要经过三层设备（路由器或三层交换机）才能通信。这样做的好处是：减少广播风暴、提升安全、并且不用受物理位置限制，人换座位也不必重新布线。配置时记住三个要点：创建 VLAN、把端口划入对应 VLAN、Trunk 链路放行需要通过的 VLAN。"
  },
  {
    date:"2026 · 10 · 20",
    title:"IP 地址与子网掩码的换算思路",
    summary:"从二进制出发，搞懂网段、主机位和 /24 到底是什么意思。",
    tags:["网络工程","IP","二进制"],
    full:"IPv4 是 32 位，分成网络位和主机位。子网掩码里连续的 1 对应网络位，0 对应主机位。比如 255.255.255.0 就是前 24 位为网络位，写作 /24，剩下 8 位是主机位，可容纳 256 个地址，去掉网络地址和广播地址，可用主机 254 个。判断两个 IP 是否在同一网段，只要把各自 IP 和掩码做按位与，结果相同就在同一网段。"
  },
  {
    date:"2026 · 09 · 15",
    title:"第一次认真拍夜景的几点心得",
    summary:"关于三脚架、ISO、快门和耐心，照片是等出来的。",
    tags:["摄影","夜景"],
    full:"夜景最忌讳高 ISO 带来的噪点。有三脚架时，把 ISO 压到 100，用慢快门让画面进光充足，光圈收到 f/8 左右保证锐度。没有三脚架就找栏杆、台阶当支撑，开启延时自拍避免按快门的抖动。另外，蓝调时刻（日落后约半小时）天空还留一点颜色，比全黑之后拍更有层次。"
  },
  {
    date:"2026 · 08 · 30",
    title:"Linux 目录结构速记",
    summary:"/etc、/var、/home、/usr 各自装什么，一张图理清。",
    tags:["Linux","学习笔记"],
    full:"/etc 放系统配置文件；/var 放经常变化的数据，如日志 /var/log；/home 是普通用户的家目录；/usr 放应用程序和共享资源；/root 是管理员的家目录；/tmp 是临时文件；/bin 和 /sbin 放基础命令。理解目录的职责划分，排查问题时就知道该去哪找配置和日志。"
  }
];

/* ===== 渲染相册 ===== */
const galleryBox = document.getElementById('galleryBox');
PHOTOS.forEach((p,i)=>{
  const card = document.createElement('div');
  card.className = 'photo-card';
  card.innerHTML =
    '<img src="'+p.src+'" alt="'+p.title+'" loading="lazy">'+
    '<div class="photo-meta"><h3>'+p.title+'</h3><p>'+p.place+'</p></div>';
  card.addEventListener('click',()=>openLightbox(i));
  galleryBox.appendChild(card);
});

/* ===== 渲染笔记 ===== */
const notesBox = document.getElementById('notesBox');
NOTES.forEach((n)=>{
  const card = document.createElement('article');
  card.className = 'note-card';
  const tags = n.tags.map(t=>'<span class="tag">'+t+'</span>').join('');
  card.innerHTML =
    '<div class="note-date">'+n.date+'</div>'+
    '<h3>'+n.title+'</h3>'+
    '<p class="note-summary">'+n.summary+'</p>'+
    '<div class="note-full">'+n.full+'</div>'+
    '<div class="note-tags">'+tags+'</div>'+
    '<button class="note-toggle">展开阅读</button>';
  const toggle = card.querySelector('.note-toggle');
  toggle.addEventListener('click',()=>{
    const open = card.classList.toggle('expanded');
    toggle.textContent = open ? '收起' : '展开阅读';
  });
  notesBox.appendChild(card);
});

/* ===== Lightbox 逻辑 ===== */
const lightbox = document.getElementById('lightbox');
const lbImg = document.getElementById('lbImg');
const lbCap = document.getElementById('lbCap');
let current = 0;

function openLightbox(i){
  current = i;
  updateLightbox();
  lightbox.classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeLightbox(){
  lightbox.classList.remove('open');
  document.body.style.overflow = '';
}
function updateLightbox(){
  const p = PHOTOS[current];
  lbImg.src = p.src;
  lbImg.alt = p.title;
  lbCap.textContent = p.title + ' · ' + p.place;
}
function step(d){
  current = (current + d + PHOTOS.length) % PHOTOS.length;
  updateLightbox();
}
document.getElementById('lbClose').addEventListener('click',closeLightbox);
document.getElementById('lbPrev').addEventListener('click',()=>step(-1));
document.getElementById('lbNext').addEventListener('click',()=>step(1));
lightbox.addEventListener('click',(e)=>{ if(e.target===lightbox) closeLightbox(); });
document.addEventListener('keydown',(e)=>{
  if(!lightbox.classList.contains('open')) return;
  if(e.key==='Escape') closeLightbox();
  if(e.key==='ArrowLeft') step(-1);
  if(e.key==='ArrowRight') step(1);
});

/* ===== 移动端菜单 ===== */
const menuBtn = document.getElementById('menuBtn');
const navLinks = document.getElementById('navLinks');
menuBtn.addEventListener('click',()=>navLinks.classList.toggle('open'));
navLinks.querySelectorAll('a').forEach(a=>{
  a.addEventListener('click',()=>navLinks.classList.remove('open'));
});
</script>
</body>
</html>
