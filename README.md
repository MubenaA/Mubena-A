<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LegalEase | AI-Powered Legal Document Generator</title>
<style>
:root{--navy:#102a43;--blue:#2563eb;--cyan:#06b6d4;--bg:#f5f8fc;--card:#fff;--text:#172033;--muted:#667085;--border:#dce3ed;--success:#0f766e}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;font-family:Inter,Segoe UI,Arial,sans-serif;background:var(--bg);color:var(--text)}
header{position:sticky;top:0;z-index:20;background:rgba(255,255,255,.96);backdrop-filter:blur(10px);border-bottom:1px solid var(--border)}
nav{max-width:1180px;margin:auto;display:flex;align-items:center;justify-content:space-between;padding:15px 20px}
.logo{font-size:25px;font-weight:800;color:var(--navy)}.logo span{color:var(--blue)}
nav a{color:#475467;text-decoration:none;margin-left:20px;font-weight:600;font-size:14px}nav a:hover{color:var(--blue)}
.hero{background:linear-gradient(135deg,#0d2742,#173f72 55%,#0e7490);color:#fff;padding:76px 20px}
.hero-inner{max-width:1180px;margin:auto;display:grid;grid-template-columns:1.3fr .7fr;gap:45px;align-items:center}
.badge{display:inline-block;padding:7px 12px;border:1px solid rgba(255,255,255,.25);border-radius:99px;background:rgba(255,255,255,.1);font-size:13px;font-weight:700}
h1{font-size:54px;line-height:1.04;margin:18px 0}.hero p{font-size:18px;line-height:1.7;color:#dbeafe;max-width:680px}
.btn{border:0;border-radius:10px;padding:12px 17px;font-weight:750;cursor:pointer;text-decoration:none;display:inline-block;margin:6px 5px 6px 0}
.primary{background:var(--blue);color:#fff}.secondary{background:#fff;color:var(--navy)}.ghost{background:#eaf1ff;color:#174ea6}
.hero .primary{background:#fff;color:#12345b}.hero .secondary{background:transparent;color:#fff;border:1px solid rgba(255,255,255,.45)}
.hero-card{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);border-radius:18px;padding:25px;box-shadow:0 20px 50px rgba(0,0,0,.16)}
.hero-card h3{margin-top:0}.check{padding:10px 0;border-bottom:1px solid rgba(255,255,255,.13)}
section{max-width:1180px;margin:auto;padding:65px 20px}.section-title{font-size:32px;margin:0 0 8px;color:var(--navy)}.section-sub{color:var(--muted);margin:0 0 28px}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:15px}.stat,.card,.step,.panel{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:22px;box-shadow:0 8px 25px rgba(16,42,67,.05)}
.stat strong{display:block;font-size:28px;color:var(--blue)}.stat span{color:var(--muted);font-size:14px}
.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}.icon{font-size:30px}.card h3{margin:10px 0 7px}.card p{color:var(--muted);line-height:1.6;font-size:14px}
.steps{display:grid;grid-template-columns:repeat(5,1fr);gap:14px}.step{text-align:center}.num{width:42px;height:42px;border-radius:50%;background:#eaf1ff;color:var(--blue);display:grid;place-items:center;margin:auto;font-weight:800}
.generator-wrap{background:#eef5ff;border-top:1px solid #d9e7fb;border-bottom:1px solid #d9e7fb}
.workspace{display:grid;grid-template-columns:360px 1fr;gap:20px}.panel h3{margin-top:0}.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
label{display:block;font-weight:700;font-size:13px;margin-bottom:6px;color:#344054}input,select,textarea{width:100%;padding:11px 12px;border:1px solid #cfd8e3;border-radius:9px;background:#fff;font:inherit}textarea{min-height:100px;resize:vertical}.full{grid-column:1/-1}
.progress{height:8px;background:#e7edf5;border-radius:99px;overflow:hidden;margin:15px 0}.progress div{height:100%;width:33%;background:linear-gradient(90deg,var(--blue),var(--cyan));transition:.25s}
.preview{min-height:520px;background:#fff;border:1px solid #d5dce7;border-radius:10px;padding:38px;white-space:pre-wrap;line-height:1.75;box-shadow:0 12px 30px rgba(16,42,67,.08)}
.preview.empty{display:grid;place-items:center;color:#98a2b3;text-align:center}
.toolrow{display:flex;flex-wrap:wrap;gap:6px;margin-top:15px}.small{font-size:12px;color:var(--muted);line-height:1.5}
.history{display:grid;gap:10px}.history-item{display:flex;justify-content:space-between;gap:15px;align-items:center;border:1px solid var(--border);background:#fff;border-radius:10px;padding:13px}
.history-item small{color:var(--muted)}.history-actions button{border:0;background:none;color:var(--blue);font-weight:700;cursor:pointer}
.notice{padding:12px 14px;background:#fff8e7;border:1px solid #f3d58b;border-radius:10px;color:#76510b;font-size:13px;line-height:1.5}
details{background:#fff;border:1px solid var(--border);border-radius:10px;padding:15px;margin:9px 0}summary{cursor:pointer;font-weight:700}
footer{background:#0d1f33;color:#dce7f5;text-align:center;padding:30px 20px}.disclaimer{max-width:900px;margin:10px auto 0;color:#a9bad0;font-size:12px;line-height:1.6}
.toast{position:fixed;right:20px;bottom:20px;background:#102a43;color:#fff;padding:12px 16px;border-radius:10px;display:none;z-index:30}
@media(max-width:900px){.hero-inner,.workspace{grid-template-columns:1fr}.cards,.stats{grid-template-columns:1fr 1fr}.steps{grid-template-columns:1fr 1fr}h1{font-size:42px}}
@media(max-width:620px){nav a{display:none}.cards,.stats,.steps,.form-grid{grid-template-columns:1fr}.full{grid-column:auto}.preview{padding:22px}}
@media print{header,.hero,section:not(#generator),.toolrow,.notice,footer,.sidebar-actions{display:none!important}.generator-wrap{border:0;background:#fff}.workspace{display:block}.preview{box-shadow:none;border:0;padding:0;min-height:0}}
</style>
</head>
<body>
<header>
<nav>
<div class="logo">Legal<span>Ease</span></div>
<div><a href="#home">Home</a><a href="#documents">Documents</a><a href="#generator">AI Generator</a><a href="#history">My Documents</a><a href="#faq">FAQ</a></div>
</nav>
</header>

<main>
<section class="hero" id="home">
<div class="hero-inner">
<div>
<span class="badge">Generative AI with Google • Project Prototype</span>
<h1>Legal Documents, Made Easier.</h1>
<p>LegalEase is an AI-powered legal document generation platform concept. Users provide structured information, the system transforms it into a professional draft, and the result can be reviewed, edited, saved and exported.</p>
<a class="btn primary" href="#generator">Start Creating</a>
<a class="btn secondary" href="#documents">Explore Documents</a>
</div>
<div class="hero-card">
<h3>LegalEase Workflow</h3>
<div class="check">✓ Choose the right document type</div>
<div class="check">✓ Complete guided information fields</div>
<div class="check">✓ Generate a structured draft</div>
<div class="check">✓ Review & edit before use</div>
<div class="check">✓ Save locally & export to PDF</div>
</div>
</div>
</section>

<section>
<div class="stats">
<div class="stat"><strong>06</strong><span>Document categories</span></div>
<div class="stat"><strong>AI</strong><span>Generation workflow</span></div>
<div class="stat"><strong>100%</strong><span>Browser-based prototype</span></div>
<div class="stat"><strong>3 Mo</strong><span>Project-ready local use</span></div>
</div>
</section>

<section id="documents">
<h2 class="section-title">Document Library</h2>
<p class="section-sub">Choose a category and LegalEase will load the relevant information fields.</p>
<div class="cards">
<div class="card"><div class="icon">🏠</div><h3>Rental Agreement</h3><p>Property, rent, deposit, tenancy, utilities, maintenance and permitted-use details.</p><button class="btn ghost" onclick="choose('rental')">Use Template</button></div>
<div class="card"><div class="icon">💼</div><h3>Employment Agreement</h3><p>Employer, employee, role, salary, work location, probation, leave and termination terms.</p><button class="btn ghost" onclick="choose('employment')">Use Template</button></div>
<div class="card"><div class="icon">📝</div><h3>Affidavit</h3><p>Deponent information, purpose, statements and verification details.</p><button class="btn ghost" onclick="choose('affidavit')">Use Template</button></div>
<div class="card"><div class="icon">⚖️</div><h3>Simple Legal Notice</h3><p>Sender, recipient, subject, facts, grievance, requested action and response period.</p><button class="btn ghost" onclick="choose('notice')">Use Template</button></div>
<div class="card"><div class="icon">🔒</div><h3>Confidentiality Agreement</h3><p>Confidential information, permitted use, protection duties, exclusions and duration.</p><button class="btn ghost" onclick="choose('confidentiality')">Use Template</button></div>
<div class="card"><div class="icon">🤝</div><h3>Non-Disclosure Agreement (NDA)</h3><p>Business purpose, covered information, access, security, confidentiality and return obligations.</p><button class="btn ghost" onclick="choose('nda')">Use Template</button></div>
</div>
</section>

<section>
<h2 class="section-title">How LegalEase Works</h2>
<p class="section-sub">A clear five-stage workflow for the AI-powered project.</p>
<div class="steps">
<div class="step"><div class="num">1</div><h3>Select</h3><p>Pick a document category.</p></div>
<div class="step"><div class="num">2</div><h3>Input</h3><p>Enter structured facts.</p></div>
<div class="step"><div class="num">3</div><h3>Generate</h3><p>Build the draft.</p></div>
<div class="step"><div class="num">4</div><h3>Review</h3><p>Edit before use.</p></div>
<div class="step"><div class="num">5</div><h3>Export</h3><p>Save or print PDF.</p></div>
</div>
</section>

<div class="generator-wrap" id="generator">
<section>
<h2 class="section-title">AI Legal Document Generator</h2>
<p class="section-sub">Guided generation workspace — designed for your project demonstration and repeated use.</p>
<div class="workspace">
<div class="panel">
<h3>1. Document Details</h3>
<label>Document Type</label>
<select id="type" onchange="loadFields()">
<option value="rental">Rental Agreement</option><option value="employment">Employment Agreement</option><option value="affidavit">Affidavit</option><option value="notice">Simple Legal Notice</option><option value="confidentiality">Confidentiality Agreement</option><option value="nda">Non-Disclosure Agreement (NDA)</option>
</select>
<div class="progress"><div id="progress"></div></div>
<p class="small" id="fieldCount"></p>
<div id="fields"></div>
<div class="sidebar-actions">
<button class="btn primary" onclick="generate()">✨ Generate AI Draft</button>
<button class="btn ghost" onclick="saveDraft()">💾 Save Draft</button>
<button class="btn" onclick="clearForm()">Clear Form</button>
</div>
<div class="notice">Project note: this prototype generates structured drafts from user-provided information. It does not verify facts or determine legal validity.</div>
</div>

<div class="panel">
<h3>2. AI-Generated Document Preview</h3>
<div id="preview" class="preview empty">Your generated legal document will appear here.<br><br>Fill the required information and select “Generate AI Draft”.</div>
<div class="toolrow">
<button class="btn primary" onclick="copyDraft()">Copy</button>
<button class="btn ghost" onclick="window.print()">Print / Save PDF</button>
<button class="btn ghost" onclick="downloadTxt()">Download .TXT</button>
</div>
<p class="small">Tip: You can edit the generated content directly in the preview before printing.</p>
</div>
</div>
</section>
</div>

<section id="history">
<h2 class="section-title">My Documents</h2>
<p class="section-sub">Saved drafts are stored in this browser using local storage, so you can reuse the website during your project period on the same browser/device.</p>
<div id="historyList" class="history"></div>
</section>

<section id="faq">
<h2 class="section-title">FAQ</h2>
<details><summary>What is LegalEase?</summary><p>LegalEase is a Generative AI project concept for converting structured user inputs into readable legal-document drafts.</p></details>
<details><summary>Is this a real legal service?</summary><p>No. It is a project prototype. Generated documents should be reviewed by an appropriately qualified legal professional before real-world use.</p></details>
<details><summary>Will my saved drafts remain?</summary><p>Saved drafts use browser localStorage. They normally remain on the same browser/device until its site data is cleared. This version does not provide cloud backup.</p></details>
<details><summary>Can I use the website for three months?</summary><p>Yes. There is no built-in expiry date. For dependable project use, keep a backup copy of the HTML file and export important documents as PDF/TXT.</p></details>
<details><summary>Is the AI API connected?</summary><p>This version contains the complete AI-style generation workflow and is designed so a Gemini API/backend can be connected later. The current standalone file does not expose an API key or require a server.</p></details>
</section>
</main>

<footer>
<strong>LegalEase</strong> — AI-Powered Legal Document Generator
<div class="disclaimer">Educational project prototype. This website does not provide legal advice, verify facts, or guarantee legal validity. Document requirements may vary by jurisdiction, transaction and purpose. Review generated content with a qualified legal professional before signing or relying on it.</div>
</footer>
<div class="toast" id="toast"></div>

<script>
const schemas={
rental:[
["Agreement Date","agreementDate","date"],["Landlord Full Name","landlord","text"],["Landlord Address","landlordAddress","textarea"],["Tenant Full Name","tenant","text"],["Tenant Address","tenantAddress","textarea"],["Property Address","property","textarea"],["Monthly Rent (₹)","rent","text"],["Security Deposit (₹)","deposit","text"],["Tenancy Start Date","startDate","date"],["Tenancy End Date","endDate","date"],["Notice Period","noticePeriod","text"],["Utilities / Bills","utilities","textarea"],["Maintenance Responsibilities","maintenance","textarea"],["Permitted Use","use","textarea"],["Additional Terms","additional","textarea"]],
employment:[
["Agreement Date","agreementDate","date"],["Employer / Company","employer","text"],["Employer Address","employerAddress","textarea"],["Employee Full Name","employee","text"],["Employee Address","employeeAddress","textarea"],["Job Title / Role","role","text"],["Joining Date","joiningDate","date"],["Work Location","workLocation","text"],["Salary / Compensation","salary","text"],["Working Hours","hours","text"],["Leave / Benefits","benefits","textarea"],["Probation Period","probation","text"],["Notice / Termination Terms","termination","textarea"],["Confidentiality / IP Terms","ip","textarea"],["Other Duties & Conditions","duties","textarea"]],
affidavit:[
["Date","date","date"],["Deponent Full Name","deponent","text"],["Age","age","text"],["Parent / Spouse Name","relation","text"],["Residential Address","address","textarea"],["Occupation","occupation","text"],["Purpose of Affidavit","purpose","textarea"],["Statement 1","statement1","textarea"],["Statement 2","statement2","textarea"],["Statement 3","statement3","textarea"],["Additional Statements","additional","textarea"],["Place of Verification","place","text"]],
notice:[
["Notice Date","noticeDate","date"],["Sender Name","sender","text"],["Sender Address","senderAddress","textarea"],["Recipient Name","recipient","text"],["Recipient Address","recipientAddress","textarea"],["Subject","subject","text"],["Relationship / Transaction","relationship","textarea"],["Relevant Date(s)","dates","text"],["Facts / Background","facts","textarea"],["Issue / Breach / Grievance","issue","textarea"],["Action Requested","action","textarea"],["Response Period","response","text"],["Consequences / Further Action (if applicable)","consequences","textarea"],["Attachments / Supporting Documents","attachments","textarea"],["Contact for Response","contact","text"]],
confidentiality:[
["Agreement Date","agreementDate","date"],["Disclosing Party","disclosing","text"],["Disclosing Party Address","disclosingAddress","textarea"],["Receiving Party","receiving","text"],["Receiving Party Address","receivingAddress","textarea"],["Purpose of Disclosure","purpose","textarea"],["Definition of Confidential Information","confidentialInfo","textarea"],["Permitted Use","permittedUse","textarea"],["Exclusions from Confidential Information","exclusions","textarea"],["Security / Protection Duties","security","textarea"],["Confidentiality Period","period","text"],["Return / Destruction of Information","return","textarea"],["Permitted Disclosure / Legal Requirement","legalDisclosure","textarea"],["Governing Law / Jurisdiction","law","text"],["Additional Terms","additional","textarea"]],
nda:[
["Agreement Date","agreementDate","date"],["Disclosing Party / Company","disclosing","text"],["Disclosing Party Address","disclosingAddress","textarea"],["Receiving Party / Company","receiving","text"],["Receiving Party Address","receivingAddress","textarea"],["Business / Project Purpose","purpose","textarea"],["Confidential Information Covered","confidentialInfo","textarea"],["Permitted Purpose / Use","permittedUse","textarea"],["Information Exclusions","exclusions","textarea"],["Security Measures","security","textarea"],["Employees / Representatives Access","access","textarea"],["Confidentiality Period","period","text"],["Return / Destruction","return","textarea"],["Breach / Remedies Clause (draft)","remedies","textarea"],["Governing Law / Jurisdiction","law","text"],["Additional Terms","additional","textarea"],["Disclosing Party Signatory Name","signatory1","text"],["Receiving Party Signatory Name","signatory2","text"]]
};
let lastDraft="", lastTitle="";
function choose(type){document.getElementById("type").value=type;loadFields();document.getElementById("generator").scrollIntoView({behavior:"smooth"});}
function loadFields(){
 const type=document.getElementById("type").value, box=document.getElementById("fields"), arr=schemas[type];
 box.innerHTML=arr.map((f,i)=>`<div style="margin:12px 0"><label>${f[0]}${i<2?" *":""}</label>${f[2]==="textarea"?`<textarea id="f_${f[1]}" placeholder="Enter ${f[0].toLowerCase()}"></textarea>`:`<input id="f_${f[1]}" type="${f[2]}" placeholder="Enter ${f[0].toLowerCase()}">`}</div>`).join("");
 document.getElementById("fieldCount").textContent=arr.length+" guided fields available for this document.";
 document.getElementById("progress").style.width=Math.min(92,25+arr.length*3)+"%";
}
function val(key){const e=document.getElementById("f_"+key);return e&&e.value.trim()?e.value.trim():"[Not provided]";}
function heading(s){return "\n\n"+s.toUpperCase()+"\n"+("=".repeat(Math.min(58,s.length+2)))+"\n";}
function generate(){
 const type=document.getElementById("type").value, arr=schemas[type];
 if(!val(arr[0][1])||!val(arr[1][1])){toast("Please fill the first required fields.");return;}
 const names={rental:"RENTAL AGREEMENT",employment:"EMPLOYMENT AGREEMENT",affidavit:"AFFIDAVIT",notice:"LEGAL NOTICE",confidentiality:"CONFIDENTIALITY AGREEMENT",nda:"NON-DISCLOSURE AGREEMENT (NDA)"};
 let out=names[type]+heading("DOCUMENT DETAILS");
 arr.forEach(f=>{out+=f[0]+": "+val(f[1])+"\n";});
 out+=heading("DRAFTING NOTE")+"This structured draft was generated from the information entered into LegalEase. Review names, dates, amounts, obligations, jurisdiction-specific requirements and all clauses before signing or relying on the document.\n";
 out+="\nSIGNATURES\n\nDisclosing / First Party: ______________________________\nReceiving / Second Party: _____________________________\nDate: __________________\n";
 lastDraft=out.trim();lastTitle=names[type];
 const p=document.getElementById("preview");p.classList.remove("empty");p.contentEditable="true";p.textContent=lastDraft;
 p.scrollIntoView({behavior:"smooth",block:"start"});toast("Draft generated successfully.");
}
function copyDraft(){const text=document.getElementById("preview").innerText.trim();if(!text){toast("Generate a draft first.");return;}navigator.clipboard.writeText(text);toast("Draft copied.");}
function saveDraft(){
 const text=document.getElementById("preview").innerText.trim();if(!text){toast("Generate a draft first.");return;}
 const arr=JSON.parse(localStorage.getItem("legaleaseDocs")||"[]");arr.unshift({id:Date.now(),title:lastTitle||"Legal Document",text,date:new Date().toLocaleString()});localStorage.setItem("legaleaseDocs",JSON.stringify(arr.slice(0,20)));renderHistory();toast("Draft saved to My Documents.");
}
function renderHistory(){
 const arr=JSON.parse(localStorage.getItem("legaleaseDocs")||"[]"), box=document.getElementById("historyList");
 if(!arr.length){box.innerHTML='<div class="panel">No saved drafts yet. Generate a document and click “Save Draft”.</div>';return;}
 box.innerHTML=arr.map(x=>`<div class="history-item"><div><b>${x.title}</b><br><small>${x.date}</small></div><div class="history-actions"><button onclick="openSaved(${x.id})">Open</button><button onclick="deleteSaved(${x.id})">Delete</button></div></div>`).join("");
}
function openSaved(id){const x=JSON.parse(localStorage.getItem("legaleaseDocs")||"[]").find(a=>a.id===id);if(!x)return;lastDraft=x.text;lastTitle=x.title;const p=document.getElementById("preview");p.classList.remove("empty");p.contentEditable="true";p.textContent=x.text;document.getElementById("generator").scrollIntoView({behavior:"smooth"});}
function deleteSaved(id){localStorage.setItem("legaleaseDocs",JSON.stringify(JSON.parse(localStorage.getItem("legaleaseDocs")||"[]").filter(x=>x.id!==id)));renderHistory();toast("Saved draft deleted.");}
function clearForm(){document.querySelectorAll("#fields input,#fields textarea").forEach(e=>e.value="");const p=document.getElementById("preview");p.classList.add("empty");p.contentEditable="false";p.textContent="Your generated legal document will appear here.";lastDraft="";toast("Form cleared.");}
function downloadTxt(){const text=document.getElementById("preview").innerText.trim();if(!text){toast("Generate a draft first.");return;}const a=document.createElement("a");a.href=URL.createObjectURL(new Blob([text],{type:"text/plain"}));a.download=(lastTitle||"LegalEase_Document").replace(/[^a-z0-9]+/gi,"_")+".txt";a.click();URL.revokeObjectURL(a.href);}
function toast(msg){const t=document.getElementById("toast");t.textContent=msg;t.style.display="block";clearTimeout(window._toast);window._toast=setTimeout(()=>t.style.display="none",2200);}
loadFields();renderHistory();
</script>
</body>
</html>
