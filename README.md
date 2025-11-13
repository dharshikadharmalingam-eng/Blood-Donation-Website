<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>BloodConnect — Dashboard Prototype</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">

<style>
/* ---------- Light Pink Theme Variables (From Code 1) ---------- */
:root {
  --bg: #ffeef6;
  --card: #ffffff;
  --text: #333;
  --heading: #b23a48; /* Dark Red/Pink for Headings */
  --accent: #ff4f91; /* Bright Pink Primary */
  --accent-dark: #e63b7d; /* Darker Pink for Hover/Secondary */
  --shadow: 0 4px 12px rgba(0,0,0,0.08);

  /* New variables needed for dashboard elements, adapted to the pink theme */
  --muted: #888; /* Soft gray for secondary text */
  --success: #28a745; /* Green for success */
  --error: #dc3545; /* Red for alerts */
  --border: #f2cde0; /* Light border for inputs/cards */
  --side-bg: #fff7fa; /* Slightly off-white for sidebar */
  --button-ghost-bg: #f9f9f9;
}

/* ---------- Global Reset & Fonts ---------- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  background: var(--bg);
  color: var(--text);
  line-height: 1.5;
  padding: 20px;
}

/* -------------------------------------- */
/* ---------- LAYOUT & CONTAINERS (Adapted from Code 1 & 2) ---------- */
/* -------------------------------------- */

/* Header styles adapted from Code 2 */
header{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  margin-bottom:20px;
  max-width: 1200px;
  margin: 20px auto;
  padding: 0 20px;
}
.brand {display:flex;align-items:center; gap:12px}
/* CLEANED UP: Logo is now purely styled, not using a broken img tag */
.logo{
  width:48px;height:48px;border-radius:10px;
  background:linear-gradient(135deg, var(--accent), var(--accent-dark));
  display:flex;align-items:center;justify-content:center;
  font-weight:700;color:white;
  box-shadow:var(--shadow);
  font-size: 20px;
}
nav a{color:var(--muted);text-decoration:none;margin-left:18px;font-size:14px;font-weight: 500;}
nav a:hover{color:var(--heading); font-weight: 600;}

/* Main container grid setup */
.container {
  display: grid;
  grid-template-columns: 320px 1fr;
  gap: 20px;
  align-items: start;
  max-width: 1200px;
  margin: 0 auto; /* Center the container */
}
.card {
  background: var(--card);
  box-shadow: var(--shadow);
  border-radius: 14px;
  padding: 20px;
  border: 1px solid var(--border);
}
.main {display:flex;flex-direction:column;gap:20px}

h1, h2, h3 {
  color: var(--heading);
  font-weight: 700;
  margin-bottom: 12px;
}
h2 {font-size: 24px;}
h3 {font-size: 18px;}


/* -------------------------------------- */
/* ---------- SIDEBAR (Adapted for Pink Theme) ---------- */
/* -------------------------------------- */

.sidebar{
  background:var(--side-bg);
  padding:18px;
  border-radius:12px;
  box-shadow: var(--shadow);
  border: 1px solid var(--border);
}
.section-title{font-size:13px;color:var(--heading);margin-bottom:10px;font-weight:600;}
.side-list{display:flex;flex-direction:column;gap:10px}
.side-btn{
  background:var(--card);
  padding:12px;
  border-radius:10px;
  border:1px solid var(--border);
  cursor:pointer;
  color:var(--text);
  font-size:14px;
  text-align:left;
  font-weight:500;
  transition: 0.2s;
}
.side-btn:hover {
  background: #fff0f5;
  border-color: var(--accent);
}
.side-btn .small{font-size:12px;color:var(--muted);display:block;margin-top:4px}
.small-muted{font-size:12px;color:var(--muted)}
hr {border-color: var(--border) !important;}

/* Notification box styling (adapted from Code 2) */
#notifBox div {
  background: #f0fff4 !important; /* Light green background */
  color: var(--success) !important;
  border: 1px solid #c3e6cb;
  font-size: 13px;
}

/* -------------------------------------- */
/* ---------- BUTTONS & FORMS (Adapted from Code 1 & 2) ---------- */
/* -------------------------------------- */
.btn {
  background: var(--accent);
  color: #fff;
  padding: 10px 16px;
  font-weight: 600;
  border-radius: 8px;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: 0.3s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
.btn:hover {
  background: var(--accent-dark);
  transform: translateY(-1px);
}
.btn.ghost {
  background: var(--button-ghost-bg);
  border: 1px solid var(--border);
  color: var(--text);
}
.btn.ghost:hover {
  background: #f0f0f0;
  border-color: var(--heading);
}

label{display:block;font-size:14px;color:var(--heading);margin-bottom:6px;font-weight:600;}
input[type="text"], input[type="email"], select, textarea, input[type="file"]{
  width:100%;padding:10px;border-radius:8px;
  border:1px solid var(--border);
  background:var(--card);
  color:var(--text);
  outline:none;
  font-size:14px;
  transition: border-color 0.2s;
}
input:focus, select:focus, textarea:focus {
  border-color: var(--accent);
  box-shadow: 0 0 0 2px rgba(255, 79, 145, 0.2);
}
textarea{min-height:110px;resize:vertical}
.row{display:flex;gap:12px;align-items:center}
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.muted{color:var(--muted);font-size:13px}

/* -------------------------------------- */
/* ---------- SPECIAL ELEMENTS ---------- */
/* -------------------------------------- */

/* Blog Editor Preview */
.editor{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.preview{
  background:#f9f9f9; /* Light background for code/preview */
  padding:15px;
  border-radius:8px;
  min-height:200px;
  overflow:auto;
  border: 1px dashed var(--border);
  color: var(--text);
}
/* Post list cards */
.posts-list{display:flex;flex-direction:column;gap:12px;margin-top:12px}
.post-card{
  padding:12px;
  border-radius:10px;
  background:var(--side-bg);
  border:1px solid var(--border);
  display:flex;gap:15px;align-items:flex-start
}
.post-card img{width:84px;height:64px;object-fit:cover;border-radius:6px}

/* Donor list / badges */
.donor-item{
  display:flex;gap:12px;align-items:center;justify-content:space-between;
  padding:10px;border-radius:10px;
  background:var(--side-bg);
  border: 1px solid var(--border);
}
.donor-left{display:flex;gap:10px;align-items:center}
.avatar{
  width:44px;height:44px;border-radius:8px;
  background:linear-gradient(135deg,var(--accent), var(--accent-dark));
  display:flex;align-items:center;justify-content:center;font-weight:700;color:white;
  font-size: 14px;
}
.stars{display:inline-flex;gap:2px;align-items:center}
.star{color:#ffc107;font-weight:700;font-size:18px;} /* Yellow for stars */

/* Emergency / Notifications */
.alert-list{display:flex;flex-direction:column;gap:10px}
.alert-item{
  padding:12px;border-radius:8px;
  background:#fff0f5; /* Very light pink/red for alerts */
  border: 1px solid #f8d7da;
  color: var(--error);
}

/* Small utilities */
.flex{display:flex;gap:8px;align-items:center}
.badge{padding:6px 10px;border-radius:999px;background:#f8f9fa;border:1px solid #dee2e6;color:var(--muted);font-size:12px}
.chip{background:#f9f2f5;padding:6px 10px;border-radius:8px;font-size:13px;color:var(--heading)}
.center{text-align:center}

/* Footer */
footer{margin-top:20px;color:var(--muted);font-size:13px;text-align:center}

/* Responsive Layout */
@media (max-width: 920px) {
  .container {
    grid-template-columns: 1fr;
    padding-bottom: 60px;
    gap: 15px;
  }
  header {flex-direction:column;align-items:flex-start; margin-bottom: 10px;}
  nav {margin-top: 8px;}
  nav a {margin-left: 0; margin-right: 18px;}
  .grid-2, .editor {grid-template-columns: 1fr;}
}
</style>
</head>
<body>

<header>
  <div class="brand">
    <div class="logo">BC</div>
    <div>
      <div style="font-weight:700; color:var(--heading);">BloodConnect</div>
      <div style="font-size:13px;color:var(--muted)">Dashboard</div>
    </div>
  </div>

  <nav>
    <a href="#blog">Blog</a>
    <a href="#donate">Donor Reg</a>
    <a href="#request">Request</a>
    <a href="#emergency">Emergency</a>
  </nav>
</header>

<div class="container">
  <aside class="sidebar">
    <div class="section-title">Quick Actions</div>
    <div class="side-list">
      <button class="side-btn" onclick="scrollToSection('blog')">📝 Create Blog <span class="small">Image upload & MD</span></button>
      <button class="side-btn" onclick="scrollToSection('donate')">🩸 Register as Donor <span class="small">Earn stars & badges</span></button>
      <button class="side-btn" onclick="scrollToSection('request')">📢 Request Blood <span class="small">Live match</span></button>
      <button class="side-btn" onclick="scrollToSection('emergency')">🚨 Emergency Alert <span class="small">Instant broadcast</span></button>
    </div>

    <hr style="margin:14px 0;border:0;height:1px;background:var(--border)">
    <div>
      <div class="section-title">Donor Tiers</div>
      <div class="small-muted">Donors earn stars and level badges based on donations:</div>
      <ul style="color:var(--muted);padding-left:18px;margin-top:8px;font-size: 13px;">
        <li>0-1: Bronze</li>
        <li>2-4: Silver</li>
        <li>5-9: Gold</li>
        <li>10+: Hero</li>
      </ul>
    </div>
    <hr style="margin:14px 0;border:0;height:1px;background:var(--border)">
    <div>
      <div class="section-title">Latest Notifications</div>
      <div id="notifBox" style="margin-top:10px"></div>
    </div>
  </aside>

  <main class="main">
    <section id="blog" class="card" aria-labelledby="blogTitle">
      <h2 id="blogTitle">Blog Page — Upload & Markdown Editor</h2>
      <div class="editor">
        <div>
          <label>Post Title</label>
          <input id="postTitle" placeholder="Write a catchy title..." />
          <label style="margin-top:10px">Upload Image</label>
          <input id="postImage" type="file" accept="image/*" />
          <div id="imgPreview" style="margin-top:10px"></div>

          <label style="margin-top:10px">Markdown Content</label>
          <textarea id="postMd" placeholder="Write in markdown... (use # for headings, **bold**, *italic*, - lists)" ></textarea>

          <div style="margin-top:10px" class="row">
            <button class="btn" onclick="createPost()">Publish Post</button>
            <button class="btn ghost" onclick="clearPostInputs()">Clear</button>
          </div>
        </div>

        <div>
          <div style="display:flex;justify-content:space-between;align-items:center">
            <div class="small-muted">Live Preview</div>
            <div class="chip" id="wordCount">0 words</div>
          </div>
          <div class="preview" id="previewArea"></div>
        </div>
      </div>

      <div style="margin-top:20px">
        <h3 style="font-size:18px;margin-bottom:8px">Published Posts</h3>
        <div id="postsList" class="posts-list"></div>
      </div>
    </section>

    <section id="donate" class="card">
      <h2>Donate Blood — Register</h2>
      <div class="grid-2">
        <div>
          <label>Full Name</label>
          <input id="donorName" type="text" placeholder="Your name" />

          <label style="margin-top:8px">Email</label>
          <input id="donorEmail" type="email" placeholder="name@example.com" />

          <label style="margin-top:8px">Phone</label>
          <input id="donorPhone" type="text" placeholder="+91 98765 43210" />
          <label style="margin-top:8px">City</label>
          <input id="donorCity" type="text" placeholder="Mumbai" />

          <label style="margin-top:8px">Area / Locality</label>
          <input id="donorArea" type="text" placeholder="Andheri West, Purasaiwalkam, etc." />

          <label style="margin-top:8px">Blood Group</label>
          <select id="donorBlood">

          
            <option value="">Select</option>
            <option>A+</option><option>A-</option><option>B+</option><option>B-</option>
            <option>AB+</option><option>AB-</option><option>O+</option><option>O-</option>
          </select>

          <label style="margin-top:8px">Profile Photo (optional)</label>
          <input id="donorPhoto" type="file" accept="image/*" />

          <div style="margin-top:15px" class="row">
            <button class="btn" onclick="registerDonor()">Register & Donate</button>
            <button class="btn ghost" onclick="addDonation()">Add Donation (simulate)</button>
          </div>
          <div style="margin-top:8px" class="small-muted">Note: "Register & Donate" will add donor and increment donations by 1.</div>
        </div>

        <div>
          <h3 style="font-size:18px;margin-bottom:8px">Donors</h3>
          <div id="donorList" style="display:flex;flex-direction:column;gap:10px"></div>

          <div style="margin-top:20px">
            <h3 style="font-size:18px;margin-bottom:8px">Selected Donor — Certificate</h3>
            <div id="selectedDonor" class="card" style="padding:15px;background:var(--side-bg);border:1px solid var(--border);">
              <div id="selDonorName" style="font-weight: 600;">No donor selected</div>
              <div id="selDonorInfo" class="small-muted" style="margin-top: 4px;">Click a donor's "Certificate" button to preview & print.</div>
              <div style="margin-top:10px">
                <button class="btn" onclick="printCertificate()">Print Certificate</button>
              </div>
            </div>
          </div>

        </div>
      </div>
    </section>

    <section id="request" class="card">
      <h2>Request Blood</h2>
      <div class="grid-2">
        <div>
          <label>Patient Name</label>
          <input id="reqPatient" placeholder="Patient name" />
          <label style="margin-top:8px">Required Blood Group</label>
          <select id="reqBlood">
            <option value="">Select</option>
            <option>A+</option><option>A-</option><option>B+</option><option>B-</option>
            <option>AB+</option><option>AB-</option><option>O+</option><option>O-</option>
          </select>
          <label style="margin-top:8px">City</label>
          <input id="reqCity" placeholder="City" />
          <label style="margin-top:8px">Contact Phone</label>
          <input id="reqPhone" placeholder="+91 ..." />

          <div style="margin-top:15px" class="row">
            <button class="btn" onclick="createRequest()">Send Request</button>
            <button class="btn ghost" onclick="searchDonors()">Search Donors</button>
          </div>
        </div>

        <div>
          <h3 style="font-size:18px">Live Matches</h3>
          <div id="matchList" style="display:flex;flex-direction:column;gap:8px"></div>

          <h3 style="font-size:18px;margin-top:20px">All Active Requests</h3>
          <div id="requestsList" style="display:flex;flex-direction:column;gap:8px"></div>
        </div>
      </div>
    </section>

    <section id="emergency" class="card">
      <h2>Emergency Blood Alert</h2>
      <div class="grid-2">
        <div>
          <label>Patient / Case Title</label>
          <input id="emTitle" placeholder="e.g. Urgent O+ needed — ICU" />
          <label style="margin-top:8px">Blood Group</label>
          <select id="emBlood">
            <option value="">Select</option>
            <option>A+</option><option>A-</option><option>B+</option><option>B-</option>
            <option>AB+</option><option>AB-</option><option>O+</option><option>O-</option>
          </select>
          <label style="margin-top:8px">City</label>
          <input id="emCity" placeholder="City" />
          <label style="margin-top:8px">Contact</label>
          <input id="emContact" placeholder="+91 ..." />

          <div style="margin-top:15px" class="row">
            <button class="btn" onclick="createEmergency()">Broadcast Emergency</button>
            <button class="btn ghost" onclick="clearEmergency()">Clear Last</button>
          </div>
        </div>

        <div>
          <h3 style="font-size:18px">Emergency Broadcasts</h3>
          <div id="emList" class="alert-list"></div>

          <div style="margin-top:20px;">
            <h3 style="font-size:18px">Recent Notifications</h3>
            <div id="recentNotifs" style="display:flex;flex-direction:column;gap:6px"></div>
          </div>
        </div>
      </div>
    </section>

    <footer>
      @ 2025 Blood Connect. Donate. Save Lives. Repeat.
    </footer>
  </main>
</div>

<script>
/* ============================
   Helper & Storage Utilities
   ============================ */
let currentSelectedDonorId = null;
const LS_KEYS = {
  donors: 'bc_donors',
  posts: 'bc_posts',
  requests: 'bc_requests',
  emergencies: 'bc_emergencies'
};
// NEW KEY for certificate functionality
const LS_LAST_CERTIFICATE = 'bc_last_certificate'; 

function saveToLS(key, val){
  localStorage.setItem(key, JSON.stringify(val));
}
function loadFromLS(key, def=[]){
  try{
    const v = JSON.parse(localStorage.getItem(key));
    return v ?? def;
  }catch(e){ return def; }
}
function uid(prefix='id'){ return prefix+'_'+Math.random().toString(36).slice(2,9) }

/* ============================
   Mini Markdown -> HTML (very small)
   ============================ */
function simpleMD(md){
  if(!md) return '';
  // escape HTML
  md = md.replaceAll('&','&amp;').replaceAll('<','&lt;').replaceAll('>','&gt;');

  // headings
  md = md.replace(/^###### (.*$)/gim, '<h6>$1</h6>');
  md = md.replace(/^##### (.*$)/gim, '<h5>$1</h5>');
  md = md.replace(/^#### (.*$)/gim, '<h4>$1</h4>');
  md = md.replace(/^### (.*$)/gim, '<h3>$1</h3>');
  md = md.replace(/^## (.*$)/gim, '<h2>$1</h2>');
  md = md.replace(/^# (.*$)/gim, '<h1>$1</h1>');
  // bold and italic
  md = md.replace(/\*\*(.*?)\*\*/gim, '<strong>$1</strong>');
  md = md.replace(/\*(.*?)\*/gim, '<em>$1</em>');
  // links
  md = md.replace(/\[([^\]]+)\]\(([^)]+)\)/gim, '<a href="$2" target="_blank" rel="noopener noreferrer" style="color: var(--accent); text-decoration: none;">$1</a>');
  // lists
  md = md.replace(/^\s*-\s+(.*)/gim, '<li>$1</li>');
  md = md.replace(/(<li>.*<\/li>)/gim, '<ul>$1</ul>');
  // paragraphs
  md = md.replace(/\n{2,}/gim, '</p><p>');
  md = '<p>'+md+'</p>';
  // tidy up: remove <ul> wrappers added multiple times
  md = md.replace(/<\/ul>\s*<ul>/g,'');
  return md;
}

/* ============================
   Blog: editor, preview, posts
   ============================ */
const postImageInput = document.getElementById('postImage');
const imgPreview = document.getElementById('imgPreview');
let postImageData = null;

postImageInput.addEventListener('change', (e)=>{
  const f = e.target.files[0];
  if(!f) { imgPreview.innerHTML=''; postImageData = null; return; }
  const reader = new FileReader();
  reader.onload = () => {
    postImageData = reader.result; // dataURL
    imgPreview.innerHTML = `<img src="${postImageData}" style="max-width:100%;height:120px;object-fit:cover;border-radius:8px">`;
  };
  reader.readAsDataURL(f);
});

const postMd = document.getElementById('postMd');
const previewArea = document.getElementById('previewArea');
const wordCount = document.getElementById('wordCount');

postMd.addEventListener('input', updatePreview);
document.getElementById('postTitle').addEventListener('input', updatePreview);

function updatePreview(){
  const md = document.getElementById('postMd').value;
  const title = document.getElementById('postTitle').value || 'Untitled';
  const html = `<h2 style="margin:0 0 8px 0; font-size: 1.2em;">${escapeHTML(title)}</h2>${simpleMD(md)}`;
  previewArea.innerHTML = html;
  wordCount.textContent = (md.trim().split(/\s+/).filter(Boolean).length || 0) + ' words';
}

function clearPostInputs(){
  document.getElementById('postTitle').value='';
  document.getElementById('postMd').value='';
  document.getElementById('postImage').value='';
  imgPreview.innerHTML='';
  postImageData=null;
  updatePreview();
}

function createPost(){
  const title = document.getElementById('postTitle').value.trim();
  const md = document.getElementById('postMd').value;
  if(!title || !md) { alert('Please add title and content'); return; }
  const posts = loadFromLS(LS_KEYS.posts, []);
  const p = { id: uid('post'), title, md, img: postImageData, created: Date.now() };
  posts.unshift(p);
  saveToLS(LS_KEYS.posts, posts);
  renderPosts();
  clearPostInputs();
  alert('Post published!');
}

function renderPosts(){
  const posts = loadFromLS(LS_KEYS.posts, []);
  const container = document.getElementById('postsList');
  container.innerHTML = '';
  posts.forEach(p=>{
    const el = document.createElement('div');
    el.className = 'post-card';
    const imgHTML = p.img ? `<img src="${p.img}" alt="thumb">` : `<div style="width:84px;height:64px;border-radius:6px;background:var(--border);display:flex;align-items:center;justify-content:center;color:var(--muted)">No image</div>`;
    el.innerHTML = `${imgHTML}
      <div style="flex:1">
        <div style="font-weight:700; color:var(--heading)">${escapeHTML(p.title)}</div>
        <div class="small-muted" style="font-size:13px;margin-top:4px">${new Date(p.created).toLocaleString()}</div>
        <div style="margin-top:6px;color:var(--muted);font-size:14px">${stripHtml(simpleMD(p.md)).slice(0,100)}${p.md.length>100?'...':''}</div>
      </div>
      <div style="display:flex;flex-direction:column;gap:6px;align-items:flex-end">
        <button class="btn" style="padding: 8px 12px; font-size: 13px;" onclick="viewPost('${p.id}')">View</button>
        <button class="btn ghost" style="padding: 8px 12px; font-size: 13px;" onclick="deletePost('${p.id}')">Delete</button>
      </div>
    `;
    container.appendChild(el);
  });
}
function viewPost(id){
  const posts = loadFromLS(LS_KEYS.posts, []);
  const p = posts.find(x=>x.id===id);
  if(!p) return alert('Post not found');
  const html = `<div style="padding:20px;background:var(--bg);border-radius:8px;color:var(--text); max-width: 800px; margin: auto;">
    <h1 style="color:var(--heading);">${escapeHTML(p.title)}</h1>
    <div style="color:var(--muted);margin-bottom:12px">${new Date(p.created).toLocaleString()}</div>
    ${p.img? `<img src="${p.img}" style="width:100%;max-height:320px;object-fit:cover;border-radius:8px;margin-bottom:16px">`:''}
    <div style="line-height: 1.6;">${simpleMD(p.md)}</div>
  </div>`;
  const w = window.open('', '_blank', 'noopener');
  w.document.write('<!doctype html><html><head><meta charset="utf-8"><title>Post</title><link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet"><style>body {font-family: Poppins, sans-serif; background: #f0f0f0;}</style></head><body>'+html+'</body></html>');
  w.document.close();
}
function deletePost(id){
  if(!confirm('Delete this post?')) return;
  const posts = loadFromLS(LS_KEYS.posts, []);
  saveToLS(LS_KEYS.posts, posts.filter(p=>p.id!==id));
  renderPosts();
}

/* ============================
   Donor management & Gamification (UPDATED CERTIFICATE LOGIC)
   ============================ */
function registerDonor(){
  const name = document.getElementById('donorName').value.trim();
  const email = document.getElementById('donorEmail').value.trim();
  const phone = document.getElementById('donorPhone').value.trim();
  const city = document.getElementById('donorCity').value.trim();
  const area = document.getElementById('donorArea').value.trim(); // <<< NEW FIELD
  const blood = document.getElementById('donorBlood').value;
  
  if(!name || !email || !phone || !city || !area || !blood) { alert('Please fill all donor fields, including Area'); return; }

  // photo
  const photoFile = document.getElementById('donorPhoto').files[0];
  const donorData = {name, email, phone, city, area, blood, donations: 1};

  if(photoFile){
    const reader = new FileReader();
    reader.onload = ()=>{
      addDonor({...donorData, photo: reader.result});
    };
    reader.readAsDataURL(photoFile);
  } else {
    addDonor({...donorData, photo: null});
  }

}
function addDonor(donor){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const id = uid('donor');
  donors.push({...donor,id,created:Date.now(), available: true}); // Default to available
  saveToLS(LS_KEYS.donors, donors);
  renderDonors();
  alert('Thanks! Donor registered and donation recorded.');
}

/* Simulate adding donation to a selected donor by email (quick action) */
function addDonation(){
  const email = document.getElementById('donorEmail').value.trim();
  if(!email){ alert('Enter donor email to add donation.'); return; }
  const donors = loadFromLS(LS_KEYS.donors, []);
  const d = donors.find(x=>x.email===email);
  if(!d){ alert('No donor with that email found.'); return; }
  d.donations = (d.donations || 0) + 1;
  saveToLS(LS_KEYS.donors, donors);
  renderDonors();
  alert('Donation count incremented for ' + d.name);
}

/* Render donors list */
function renderDonors(){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const list = document.getElementById('donorList');
  list.innerHTML = '';
  donors.sort((a,b)=>b.donations - a.donations);
  donors.forEach(d=>{
    const el = document.createElement('div');
    el.className = 'donor-item';
    const availabilityStyle = d.available ? 'color: var(--success); font-weight: 600;' : 'color: var(--error);';
    const buttonText = d.available ? 'Set Unavailable' : 'Set Available';

    el.innerHTML = `
      <div class="donor-left">
        <div class="avatar">${d.photo? `<img src="${d.photo}" style="width:100%;height:100%;object-fit:cover;border-radius:8px">`: d.name.split(' ').map(n=>n[0]).slice(0,2).join('')}</div>
        <div>
          <div style="font-weight:700; color: var(--heading);">${escapeHTML(d.name)} <span class="small-muted" style="font-weight:500; margin-left: 5px;">(${d.blood})</span></div>
          <div class="small-muted">${escapeHTML(d.city)} · ${escapeHTML(d.email)}</div>
          <div class="small-muted" style="margin-top: 5px;">Status: <span style="${availabilityStyle}">${d.available ? 'Available' : 'Unavailable'}</span></div>
        </div>
      </div>
      <div style="display:flex;flex-direction:column;align-items:flex-end;gap:8px">
        <div>
          <span class="small-muted">Donations:</span> <strong style="color: var(--heading)">${d.donations || 0}</strong>
        </div>
        <div style="display:flex;gap:6px">
          <button class="btn ghost" style="padding: 6px 10px; font-size: 12px;" onclick="selectDonor('${d.id}')">Select</button>
          <button class="btn" style="padding: 6px 10px; font-size: 12px;" onclick="generateCertificateFor('${d.id}')">Certificate</button>
          <button class="btn ghost" style="padding: 6px 10px; font-size: 12px;" onclick="toggleAvailability('${d.id}', this)">${buttonText}</button>
        </div>
        <div style="margin-top:6px">${renderStars(d.donations || 0)} <span class="chip">${badgeFor(d.donations || 0)}</span></div>
      </div>
    `;
    list.appendChild(el);
  });
}

/* render stars visually */
function renderStars(count){
  const n = Math.min(5, Math.floor(count/2)+1); // simple scale
  let out = '<span class="stars">';
  for(let i=0;i<n;i++) out += '<span class="star">★</span>';
  out += '</span>';
  return out;
}
function badgeFor(count){
  if(count>=10) return 'Hero';
  if(count>=5) return 'Gold';
  if(count>=2) return 'Silver';
  return 'Bronze';
}

/* Select donor for certificate */
function selectDonor(id){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const d = donors.find(x=>x.id===id);
  if(!d) return;
  currentSelectedDonorId = id;
  document.getElementById('selDonorName').innerHTML = `<strong>${escapeHTML(d.name)}</strong> (${d.blood})`;
  document.getElementById('selDonorInfo').innerText = `${d.donations||0} donations · ${d.city} · ${d.email}`;
}

/**
 * 💡 UPDATED FUNCTION: Saves donor ID and opens the new certificate.html page.
 */
function generateCertificateFor(id){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const d = donors.find(x=>x.id===id);
  if(!d) return alert('Donor not found');

  // 1. Save the donor's ID so the new certificate page can read it.
  localStorage.setItem(LS_LAST_CERTIFICATE, id); 

  // 2. Update the dashboard preview area 
  currentSelectedDonorId = d.id;
  document.getElementById('selDonorName').innerHTML = `<strong>${escapeHTML(d.name)}</strong> (${d.blood})`;
  document.getElementById('selDonorInfo').innerText = `${d.donations||0} donations · ${d.city} · ${d.email}`;

  // 3. Open the dedicated certificate page. (Requires certificate.html file)
  window.open('certificate.html', '_blank', 'noopener');
}

/**
 * 💡 UPDATED FUNCTION: Now uses the dedicated certificate page based on selected donor.
 */
function printCertificate(){
  if(!currentSelectedDonorId) return alert('No donor selected for certificate');
  
  // 1. Save the currently selected ID
  localStorage.setItem(LS_LAST_CERTIFICATE, currentSelectedDonorId);

  // 2. Open the dedicated certificate page. (Requires certificate.html file)
  window.open('certificate.html', '_blank', 'noopener');
}

/* toggle availability - updates button text in JS logic */
function toggleAvailability(id, btn){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const d = donors.find(x=>x.id===id);
  if(!d) return;
  d.available = !d.available;
  saveToLS(LS_KEYS.donors, donors);
  // Re-render to update the visual state and button text correctly
  renderDonors();
}

/* ============================
   Requests: match donors
   ============================ */
function createRequest(){
  const patient = document.getElementById('reqPatient').value.trim();
  const blood = document.getElementById('reqBlood').value;
  const city = document.getElementById('reqCity').value.trim();
  const phone = document.getElementById('reqPhone').value.trim();
  if(!patient || !blood || !city || !phone) return alert('Please fill request fields');

  const requests = loadFromLS(LS_KEYS.requests, []);
  const req = { id: uid('req'), patient, blood, city, phone, created:Date.now(), status:'open' };
  requests.unshift(req);
  saveToLS(LS_KEYS.requests, requests);
  renderRequests();
  searchDonors(true); // auto-search and notify matches
  alert('Request created & broadcasted locally.');
}

function renderRequests(){
  const requests = loadFromLS(LS_KEYS.requests, []);
  const el = document.getElementById('requestsList');
  el.innerHTML = '';
  requests.forEach(r=>{
    const div = document.createElement('div');
    div.className = 'donor-item';
    const statusColor = r.status === 'fulfilled' ? 'var(--success)' : 'var(--accent)';
    div.innerHTML = `
      <div style="display:flex;flex-direction:column">
        <div style="font-weight:700; color: var(--heading);">${escapeHTML(r.patient)} <span class="small-muted">(${r.blood})</span></div>
        <div class="small-muted">${escapeHTML(r.city)} · ${new Date(r.created).toLocaleString()}</div>
      </div>
      <div style="display:flex;gap:8px;align-items:center">
        <div class="badge" style="color: ${statusColor}; border-color: ${statusColor}44;">${r.status}</div>
        <button class="btn" style="padding: 6px 10px; font-size: 12px;" onclick="markFulfilled('${r.id}')">Mark Fulfilled</button>
        <button class="btn ghost" style="padding: 6px 10px; font-size: 12px;" onclick="removeRequest('${r.id}')">Remove</button>
      </div>
    `;
    el.appendChild(div);
  });
}

/* find donors for the topmost open request or input fields */
function searchDonors(autoClose=false){
  const blood = document.getElementById('reqBlood').value;
  const city = document.getElementById('reqCity').value.trim();
  let matches = [];
  const donors = loadFromLS(LS_KEYS.donors, []);
  donors.forEach(d=>{
    if(!blood || !city || !d.available) return; // Only match available donors
    if(d.blood === blood && d.city.toLowerCase() === city.toLowerCase()){
      matches.push(d);
    }
  });
  const list = document.getElementById('matchList');
  list.innerHTML = '';
  if(matches.length===0) list.innerHTML = '<div class="small-muted" style="padding: 10px; text-align: center;">No exact matches found (local and available).</div>';
  matches.forEach(m=>{
    const div = document.createElement('div');
    div.className = 'donor-item';
    div.innerHTML = `<div style="display:flex;gap:10px;align-items:center">
      <div class="avatar">${m.name.split(' ').map(n=>n[0]).slice(0,2).join('')}</div>
      <div><div style="font-weight:700; color: var(--heading);">${escapeHTML(m.name)}</div><div class="small-muted">${escapeHTML(m.phone)} · ${m.donations||0} donations</div></div>
    </div>
    <div><button class="btn" style="padding: 6px 10px; font-size: 12px;" onclick="notifyDonor('${m.id}')">Contact</button></div>`;
    list.appendChild(div);
  });

  // If autoClose indicates this search was triggered after creating request, notify app
  if(autoClose){
    const requests = loadFromLS(LS_KEYS.requests, []);
    const top = requests[0];
    if(top && matches.length>0){
      simulateNotification(`Found ${matches.length} local donor(s) for request (${top.blood}) in ${top.city}`);
    } else if(top){
      simulateNotification(`No AVAILABLE matches found locally for ${top.blood} in ${top.city}`);
    }
  }
}

/* Mark as fulfilled or remove */
function markFulfilled(id){
  const requests = loadFromLS(LS_KEYS.requests, []);
  const r = requests.find(x=>x.id===id);
  if(!r) return;
  r.status = 'fulfilled';
  saveToLS(LS_KEYS.requests, requests);
  renderRequests();
}
function removeRequest(id){
  if(!confirm('Remove this request?')) return;
  const requests = loadFromLS(LS_KEYS.requests, []);
  saveToLS(LS_KEYS.requests, requests.filter(x=>x.id!==id));
  renderRequests();
}

/* ============================
   Emergency alerts & broadcasts
   ============================ */
function createEmergency(){
  const title = document.getElementById('emTitle').value.trim();
  const blood = document.getElementById('emBlood').value;
  const city = document.getElementById('emCity').value.trim();
  const contact = document.getElementById('emContact').value.trim();
  if(!title || !blood || !city || !contact) return alert('Fill emergency fields');

  const em = loadFromLS(LS_KEYS.emergencies, []);
  const e = { id: uid('em'), title, blood, city, contact, created:Date.now() };
  em.unshift(e);
  saveToLS(LS_KEYS.emergencies, em);
  renderEmergencies();
  simulateBroadcast(e);
  alert('Emergency broadcast created locally.');
}
function renderEmergencies(){
  const em = loadFromLS(LS_KEYS.emergencies, []);
  const el = document.getElementById('emList');
  el.innerHTML = '';
  em.forEach(item=>{
    const div = document.createElement('div');
    div.className = 'alert-item';
    div.innerHTML = `<div style="font-weight:700">${escapeHTML(item.title)} <span class="small-muted" style="color: var(--error);">(${item.blood})</span></div>
      <div style="margin-top:6px" class="small-muted">${escapeHTML(item.city)} · ${new Date(item.created).toLocaleString()} · ${escapeHTML(item.contact)}</div>
      <div style="margin-top:10px;display:flex;gap:8px">
          <button class="btn" style="padding: 6px 10px; font-size: 12px; background: var(--error); color: white;" onclick="simulateBroadcastConfirm('${item.id}')">Acknowledge</button>
          <button class="btn ghost" style="padding: 6px 10px; font-size: 12px;" onclick="clearEmergencyById('${item.id}')">Remove</button>
      </div>
    `;
    el.appendChild(div);
  });
}
function clearEmergency(){
  const em = loadFromLS(LS_KEYS.emergencies, []);
  if(em.length===0) return;
  em.shift();
  saveToLS(LS_KEYS.emergencies, em);
  renderEmergencies();
}
function clearEmergencyById(id){
  const em = loadFromLS(LS_KEYS.emergencies, []);
  saveToLS(LS_KEYS.emergencies, em.filter(x=>x.id!==id));
  renderEmergencies();
}

function simulateBroadcast(item){
  // add to recent notifications
  const box = document.getElementById('recentNotifs');
  const d = typeof item === 'string' ? item : `EMERGENCY: ${item.title} — ${item.blood} in ${item.city}`;
  const n = document.createElement('div');
  n.className = 'badge';
  n.textContent = d;
  box.prepend(n);
  // Simulate matching donors too
  setTimeout(()=> searchDonorsForEmergency(item), 400);
}

function simulateBroadcastConfirm(id){
  const em = loadFromLS(LS_KEYS.emergencies, []);
  const item = em.find(x=>x.id===id);
  if(!item) return;
  simulateNotification(`Acknowledged emergency: ${item.title}`);
}

/* Find donors for emergency and notify */
function searchDonorsForEmergency(em){
  if(!em || !em.blood || !em.city) return;
  const donors = loadFromLS(LS_KEYS.donors, []);
  // Match ALL donors for emergency, even if not explicitly "Available"
  const matches = donors.filter(d=>d.blood===em.blood && d.city.toLowerCase()===em.city.toLowerCase());
  if(matches.length>0){
    simulateNotification(`EMERGENCY: Found ${matches.length} potential donor(s) for ${em.blood} in ${em.city}.`);
  } else {
    simulateNotification(`EMERGENCY: No local donors found for ${em.blood} in ${em.city}. Consider wider reach.`);
  }
}

/* ============================
   Notifications (simulated Email/SMS)
   ============================ */
function simulateNotification(msg){
  const box = document.getElementById('notifBox');
  const p = document.createElement('div');
  p.style.padding='10px';
  p.style.marginTop='10px';
  p.style.borderRadius='8px';
  p.style.background='linear-gradient(90deg,#f0fff4,#e6faee)';
  p.style.color='var(--success)';
  p.style.border='1px solid #c3e6cb';
  p.textContent = msg;
  box.prepend(p);

  // also show recent
  const rn = document.getElementById('recentNotifs');
  const n = document.createElement('div');
  n.className='chip';
  n.textContent = msg;
  rn.prepend(n);
}

/* manually notify a donor (simulate SMS/email) */
function notifyDonor(id){
  const donors = loadFromLS(LS_KEYS.donors, []);
  const d = donors.find(x=>x.id===id);
  if(!d) return alert('Donor not found');
  simulateNotification(`Sent simulated SMS/Email to ${d.name} (${d.phone})`);
  alert('Simulated notification sent (check Notification box).');
}

/* ============================
   Utilities & Init
   ============================ */
function escapeHTML(s){ return String(s).replaceAll('&','&amp;').replaceAll('<','&lt;').replaceAll('>','&gt;') }
function stripHtml(html){ return html.replace(/<[^>]*>?/gm, ''); }

function scrollToSection(id){
  document.getElementById(id).scrollIntoView({behavior:'smooth'});
}

/* initial render */
renderPosts();
renderDonors();
renderRequests();
renderEmergencies();

/* small convenience: expose some functions to console for dev */
window._bc = {
  load: loadFromLS, save: saveToLS, keys: LS_KEYS
};
</script>

</body>
</html>
