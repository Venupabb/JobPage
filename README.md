<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>JobFlash — Latest Job Openings</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #13131a;
    --card: #1a1a24;
    --border: #2a2a3a;
    --accent: #00e5a0;
    --accent2: #7c6fff;
    --accent3: #ff6b6b;
    --text: #e8e8f0;
    --muted: #6b6b85;
    --tag-bg: #1e1e2e;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,160,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,160,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* HEADER */
  header {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 0 24px;
  }
  .header-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
  }
  .logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.4rem;
    letter-spacing: -0.5px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .logo-dot { color: var(--accent); }
  .logo-flash {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .header-right {
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .post-btn {
    background: var(--accent);
    color: #0a0a0f;
    border: none;
    padding: 8px 18px;
    border-radius: 8px;
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.85rem;
    cursor: pointer;
    transition: all 0.2s;
    letter-spacing: 0.3px;
  }
  .post-btn:hover { background: #00ffb3; transform: translateY(-1px); }

  /* HERO */
  .hero {
    position: relative;
    z-index: 1;
    max-width: 1100px;
    margin: 0 auto;
    padding: 72px 24px 48px;
    text-align: center;
  }
  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(0,229,160,0.08);
    border: 1px solid rgba(0,229,160,0.2);
    padding: 5px 14px;
    border-radius: 100px;
    font-size: 0.78rem;
    color: var(--accent);
    font-weight: 500;
    margin-bottom: 24px;
    animation: fadeUp 0.6s ease both;
  }
  .pulse {
    width: 7px; height: 7px;
    background: var(--accent);
    border-radius: 50%;
    animation: pulse 1.5s ease infinite;
  }
  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(1.5); }
  }
  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(2.2rem, 6vw, 3.8rem);
    line-height: 1.1;
    letter-spacing: -1.5px;
    animation: fadeUp 0.6s 0.1s ease both;
    margin-bottom: 16px;
  }
  .hero h1 span {
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero p {
    color: var(--muted);
    font-size: 1.05rem;
    max-width: 480px;
    margin: 0 auto 36px;
    line-height: 1.6;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  /* SEARCH BAR */
  .search-wrap {
    max-width: 580px;
    margin: 0 auto;
    position: relative;
    animation: fadeUp 0.6s 0.3s ease both;
  }
  .search-wrap input {
    width: 100%;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 14px 50px 14px 18px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.95rem;
    outline: none;
    transition: border-color 0.2s;
  }
  .search-wrap input:focus { border-color: var(--accent); }
  .search-wrap input::placeholder { color: var(--muted); }
  .search-icon {
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--muted);
    font-size: 1.1rem;
    pointer-events: none;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* FILTERS */
  .filters {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 24px 28px;
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    position: relative;
    z-index: 1;
  }
  .filter-chip {
    padding: 7px 16px;
    border-radius: 100px;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    cursor: pointer;
    transition: all 0.2s;
  }
  .filter-chip:hover, .filter-chip.active {
    background: var(--accent);
    border-color: var(--accent);
    color: #0a0a0f;
    font-weight: 600;
  }

  /* STATS */
  .stats-bar {
    max-width: 1100px;
    margin: 0 auto 8px;
    padding: 0 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
    z-index: 1;
  }
  .stats-bar span {
    font-size: 0.85rem;
    color: var(--muted);
  }
  .stats-bar strong { color: var(--accent); }

  /* GRID */
  .jobs-grid {
    max-width: 1100px;
    margin: 0 auto;
    padding: 16px 24px 80px;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 16px;
    position: relative;
    z-index: 1;
  }

  /* JOB CARD */
  .job-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 22px;
    display: flex;
    flex-direction: column;
    gap: 14px;
    transition: all 0.25s;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.5s ease both;
  }
  .job-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.25s;
  }
  .job-card:hover {
    border-color: rgba(0,229,160,0.25);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(0,0,0,0.4);
  }
  .job-card:hover::before { opacity: 1; }

  .card-top {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 12px;
  }
  .company-logo {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1rem;
    flex-shrink: 0;
  }
  .badge-new {
    background: rgba(0,229,160,0.1);
    border: 1px solid rgba(0,229,160,0.25);
    color: var(--accent);
    padding: 3px 10px;
    border-radius: 100px;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    white-space: nowrap;
  }
  .badge-hot {
    background: rgba(255,107,107,0.1);
    border: 1px solid rgba(255,107,107,0.25);
    color: var(--accent3);
    padding: 3px 10px;
    border-radius: 100px;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    white-space: nowrap;
  }
  .badge-remote {
    background: rgba(124,111,255,0.1);
    border: 1px solid rgba(124,111,255,0.25);
    color: var(--accent2);
    padding: 3px 10px;
    border-radius: 100px;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    white-space: nowrap;
  }

  .job-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1rem;
    line-height: 1.3;
    color: var(--text);
  }
  .company-name {
    font-size: 0.85rem;
    color: var(--muted);
    margin-top: 2px;
  }

  .job-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .meta-item {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 0.8rem;
    color: var(--muted);
  }
  .meta-item svg { flex-shrink: 0; }

  .job-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .tag {
    background: var(--tag-bg);
    border: 1px solid var(--border);
    color: var(--muted);
    padding: 3px 10px;
    border-radius: 6px;
    font-size: 0.75rem;
  }

  .card-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 4px;
    padding-top: 14px;
    border-top: 1px solid var(--border);
  }
  .salary {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    color: var(--accent);
  }
  .apply-btn {
    background: transparent;
    border: 1px solid var(--accent);
    color: var(--accent);
    padding: 7px 16px;
    border-radius: 8px;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 0.8rem;
    cursor: pointer;
    text-decoration: none;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 5px;
  }
  .apply-btn:hover {
    background: var(--accent);
    color: #0a0a0f;
  }

  /* MODAL */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    backdrop-filter: blur(6px);
    z-index: 200;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  .modal-overlay.open { display: flex; }
  .modal {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 32px;
    width: 100%;
    max-width: 520px;
    max-height: 90vh;
    overflow-y: auto;
  }
  .modal h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.4rem;
    margin-bottom: 6px;
  }
  .modal p { color: var(--muted); font-size: 0.9rem; margin-bottom: 24px; }
  .form-group { margin-bottom: 16px; }
  .form-group label {
    display: block;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--muted);
    margin-bottom: 6px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .form-group input, .form-group select, .form-group textarea {
    width: 100%;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 11px 14px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.2s;
  }
  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus { border-color: var(--accent); }
  .form-group textarea { resize: vertical; min-height: 80px; }
  .form-group select option { background: var(--card); }
  .modal-actions {
    display: flex;
    gap: 10px;
    margin-top: 8px;
  }
  .btn-cancel {
    flex: 1;
    padding: 11px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-cancel:hover { border-color: var(--text); color: var(--text); }
  .btn-submit {
    flex: 2;
    padding: 11px;
    border-radius: 10px;
    border: none;
    background: var(--accent);
    color: #0a0a0f;
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-submit:hover { background: #00ffb3; }

  /* EMPTY */
  .empty {
    grid-column: 1/-1;
    text-align: center;
    padding: 60px 20px;
    color: var(--muted);
  }
  .empty h3 {
    font-family: 'Syne', sans-serif;
    font-size: 1.2rem;
    margin-bottom: 8px;
    color: var(--text);
  }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 24px;
    text-align: center;
    color: var(--muted);
    font-size: 0.82rem;
    position: relative;
    z-index: 1;
  }
  footer strong { color: var(--accent); }

  @media (max-width: 600px) {
    .jobs-grid { grid-template-columns: 1fr; }
    .hero { padding: 48px 20px 32px; }
    .modal { padding: 24px; }
  }
</style>
</head>
<body>

<header>
  <div class="header-inner">
    <div class="logo">
      <span class="logo-flash">Job</span><span class="logo-dot">Flash</span>
    </div>
    <div class="header-right">
      <button class="post-btn" onclick="openModal()">+ Post a Job</button>
    </div>
  </div>
</header>

<section class="hero">
  <div class="hero-badge">
    <div class="pulse"></div>
    Updated Daily · 100% Free
  </div>
  <h1>Find Your <span>Dream Job</span><br/>Posted Fresh Daily</h1>
  <p>Latest job openings curated for you. Apply directly — no sign-up needed.</p>
  <div class="search-wrap">
    <input type="text" id="searchInput" placeholder="Search jobs, companies, skills..." oninput="filterJobs()"/>
    <span class="search-icon">🔍</span>
  </div>
</section>

<div class="filters">
  <button class="filter-chip active" onclick="setFilter('All', this)">All Jobs</button>
  <button class="filter-chip" onclick="setFilter('Remote', this)">🌐 Remote</button>
  <button class="filter-chip" onclick="setFilter('Full-time', this)">💼 Full-time</button>
  <button class="filter-chip" onclick="setFilter('Part-time', this)">⏰ Part-time</button>
  <button class="filter-chip" onclick="setFilter('Internship', this)">🎓 Internship</button>
  <button class="filter-chip" onclick="setFilter('Fresher', this)">⭐ Fresher</button>
</div>

<div class="stats-bar">
  <span id="jobCount"><strong>0</strong> jobs found</span>
  <span>Last updated: <strong id="lastUpdated"></strong></span>
</div>

<div class="jobs-grid" id="jobsGrid"></div>

<!-- POST JOB MODAL -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
    <h2>Post a New Job</h2>
    <p>Fill in the details and help someone find their next opportunity.</p>
    <div class="form-group">
      <label>Job Title *</label>
      <input type="text" id="fTitle" placeholder="e.g. Frontend Developer"/>
    </div>
    <div class="form-group">
      <label>Company Name *</label>
      <input type="text" id="fCompany" placeholder="e.g. Google"/>
    </div>
    <div class="form-group">
      <label>Location</label>
      <input type="text" id="fLocation" placeholder="e.g. Mumbai / Remote"/>
    </div>
    <div class="form-group">
      <label>Job Type</label>
      <select id="fType">
        <option>Full-time</option>
        <option>Part-time</option>
        <option>Remote</option>
        <option>Internship</option>
        <option>Fresher</option>
      </select>
    </div>
    <div class="form-group">
      <label>Salary / Stipend</label>
      <input type="text" id="fSalary" placeholder="e.g. ₹8–12 LPA or Not Disclosed"/>
    </div>
    <div class="form-group">
      <label>Skills (comma separated)</label>
      <input type="text" id="fSkills" placeholder="e.g. React, Node.js, AWS"/>
    </div>
    <div class="form-group">
      <label>Apply Link *</label>
      <input type="url" id="fLink" placeholder="https://careers.company.com/apply"/>
    </div>
    <div class="form-group">
      <label>Short Description</label>
      <textarea id="fDesc" placeholder="Brief about the role, requirements..."></textarea>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal()">Cancel</button>
      <button class="btn-submit" onclick="submitJob()">🚀 Post Job</button>
    </div>
  </div>
</div>

<footer>
  Made with ❤️ by <strong>JobFlash</strong> · Helping people find jobs every day
</footer>

<script>
  // ── Sample jobs (you can delete these and add your own) ──
  let jobs = [
    {
      id: 1,
      title: "Frontend Developer",
      company: "TechCorp India",
      location: "Bengaluru / Remote",
      type: "Full-time",
      salary: "₹8–14 LPA",
      skills: ["React", "JavaScript", "CSS"],
      link: "https://www.naukri.com",
      desc: "Build modern web interfaces for millions of users. 2+ years exp preferred.",
      badge: "new",
      logo: "TC",
      logoColor: "#00e5a0",
      logoBg: "rgba(0,229,160,0.12)",
      postedDate: new Date()
    },
    {
      id: 2,
      title: "Data Analyst",
      company: "Infosys",
      location: "Pune",
      type: "Full-time",
      salary: "₹6–10 LPA",
      skills: ["SQL", "Excel", "Power BI"],
      link: "https://www.infosys.com/careers",
      desc: "Analyze business data and drive insights for key decisions.",
      badge: "hot",
      logo: "IN",
      logoColor: "#ff6b6b",
      logoBg: "rgba(255,107,107,0.12)",
      postedDate: new Date()
    },
    {
      id: 3,
      title: "Python Developer",
      company: "Wipro",
      location: "Remote",
      type: "Remote",
      salary: "₹10–18 LPA",
      skills: ["Python", "Django", "REST APIs"],
      link: "https://careers.wipro.com",
      desc: "Work on backend systems and automation. 3+ years Python experience needed.",
      badge: "remote",
      logo: "WP",
      logoColor: "#7c6fff",
      logoBg: "rgba(124,111,255,0.12)",
      postedDate: new Date()
    },
    {
      id: 4,
      title: "IT Support Engineer",
      company: "HCL Technologies",
      location: "Noida",
      type: "Full-time",
      salary: "₹4–7 LPA",
      skills: ["Networking", "Windows", "Troubleshooting"],
      link: "https://www.hcltech.com/careers",
      desc: "Provide L1/L2 IT support to enterprise clients. Fresher-friendly.",
      badge: "new",
      logo: "HC",
      logoColor: "#ffd166",
      logoBg: "rgba(255,209,102,0.12)",
      postedDate: new Date()
    },
    {
      id: 5,
      title: "HR Intern",
      company: "Swiggy",
      location: "Bengaluru",
      type: "Internship",
      salary: "₹15,000/mo",
      skills: ["Communication", "MS Office", "Recruitment"],
      link: "https://careers.swiggy.com",
      desc: "6-month HR internship. Great learning opportunity at a top startup.",
      badge: "new",
      logo: "SW",
      logoColor: "#ff9a3c",
      logoBg: "rgba(255,154,60,0.12)",
      postedDate: new Date()
    },
    {
      id: 6,
      title: "Cloud Engineer",
      company: "Amazon (AWS)",
      location: "Hyderabad / Remote",
      type: "Full-time",
      salary: "₹20–35 LPA",
      skills: ["AWS", "Terraform", "Linux"],
      link: "https://amazon.jobs",
      desc: "Design and manage cloud infrastructure on AWS. 4+ years required.",
      badge: "hot",
      logo: "AM",
      logoColor: "#ff6b6b",
      logoBg: "rgba(255,107,107,0.12)",
      postedDate: new Date()
    }
  ];

  let activeFilter = 'All';

  function formatDate(d) {
    const now = new Date();
    const diff = Math.floor((now - d) / 60000);
    if (diff < 2) return 'Just now';
    if (diff < 60) return diff + 'm ago';
    if (diff < 1440) return Math.floor(diff/60) + 'h ago';
    return Math.floor(diff/1440) + 'd ago';
  }

  function getBadgeHTML(badge) {
    if (badge === 'new') return '<span class="badge-new">✦ NEW</span>';
    if (badge === 'hot') return '<span class="badge-hot">🔥 HOT</span>';
    if (badge === 'remote') return '<span class="badge-remote">🌐 REMOTE</span>';
    return '';
  }

  function renderJobs() {
    const query = document.getElementById('searchInput').value.toLowerCase();
    const grid = document.getElementById('jobsGrid');

    let filtered = jobs.filter(j => {
      const matchFilter = activeFilter === 'All' || j.type === activeFilter;
      const matchSearch = !query ||
        j.title.toLowerCase().includes(query) ||
        j.company.toLowerCase().includes(query) ||
        j.skills.some(s => s.toLowerCase().includes(query)) ||
        j.location.toLowerCase().includes(query);
      return matchFilter && matchSearch;
    });

    document.getElementById('jobCount').innerHTML = `<strong>${filtered.length}</strong> job${filtered.length !== 1 ? 's' : ''} found`;

    if (filtered.length === 0) {
      grid.innerHTML = `<div class="empty"><h3>No jobs found</h3><p>Try a different search or filter.</p></div>`;
      return;
    }

    grid.innerHTML = filtered.map((j, i) => `
      <div class="job-card" style="animation-delay:${i*0.06}s">
        <div class="card-top">
          <div style="display:flex;align-items:center;gap:12px;flex:1;min-width:0">
            <div class="company-logo" style="background:${j.logoBg};color:${j.logoColor}">${j.logo}</div>
            <div style="min-width:0">
              <div class="job-title">${j.title}</div>
              <div class="company-name">${j.company}</div>
            </div>
          </div>
          ${getBadgeHTML(j.badge)}
        </div>

        <div class="job-meta">
          <span class="meta-item">
            <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
            ${j.location}
          </span>
          <span class="meta-item">
            <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><rect x="2" y="7" width="20" height="14" rx="2"/><path d="M16 7V5a2 2 0 00-2-2h-4a2 2 0 00-2 2v2"/></svg>
            ${j.type}
          </span>
          <span class="meta-item">
            <svg width="13" height="13" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/></svg>
            ${formatDate(j.postedDate)}
          </span>
        </div>

        ${j.desc ? `<p style="font-size:0.83rem;color:var(--muted);line-height:1.5">${j.desc}</p>` : ''}

        <div class="job-tags">
          ${j.skills.map(s => `<span class="tag">${s}</span>`).join('')}
        </div>

        <div class="card-footer">
          <span class="salary">${j.salary || 'Not Disclosed'}</span>
          <a class="apply-btn" href="${j.link}" target="_blank" rel="noopener">
            Apply Now
            <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </a>
        </div>
      </div>
    `).join('');
  }

  function filterJobs() { renderJobs(); }

  function setFilter(f, el) {
    activeFilter = f;
    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
    el.classList.add('active');
    renderJobs();
  }

  function openModal() {
    document.getElementById('modalOverlay').classList.add('open');
  }
  function closeModal() {
    document.getElementById('modalOverlay').classList.remove('open');
    ['fTitle','fCompany','fLocation','fSalary','fSkills','fLink','fDesc'].forEach(id => {
      document.getElementById(id).value = '';
    });
  }

  document.getElementById('modalOverlay').addEventListener('click', function(e) {
    if (e.target === this) closeModal();
  });

  const logoColors = [
    { color: '#00e5a0', bg: 'rgba(0,229,160,0.12)' },
    { color: '#7c6fff', bg: 'rgba(124,111,255,0.12)' },
    { color: '#ff6b6b', bg: 'rgba(255,107,107,0.12)' },
    { color: '#ffd166', bg: 'rgba(255,209,102,0.12)' },
    { color: '#ff9a3c', bg: 'rgba(255,154,60,0.12)' },
  ];

  function submitJob() {
    const title = document.getElementById('fTitle').value.trim();
    const company = document.getElementById('fCompany').value.trim();
    const link = document.getElementById('fLink').value.trim();

    if (!title || !company || !link) {
      alert('Please fill in Title, Company, and Apply Link at minimum.');
      return;
    }

    const colorPick = logoColors[Math.floor(Math.random() * logoColors.length)];
    const newJob = {
      id: Date.now(),
      title,
      company,
      location: document.getElementById('fLocation').value.trim() || 'Not specified',
      type: document.getElementById('fType').value,
      salary: document.getElementById('fSalary').value.trim() || 'Not Disclosed',
      skills: document.getElementById('fSkills').value.split(',').map(s => s.trim()).filter(Boolean),
      link,
      desc: document.getElementById('fDesc').value.trim(),
      badge: 'new',
      logo: company.slice(0,2).toUpperCase(),
      logoColor: colorPick.color,
      logoBg: colorPick.bg,
      postedDate: new Date()
    };

    jobs.unshift(newJob);
    closeModal();
    activeFilter = 'All';
    document.querySelectorAll('.filter-chip').forEach((c,i) => {
      c.classList.toggle('active', i === 0);
    });
    document.getElementById('searchInput').value = '';
    renderJobs();
  }

  // Set last updated time
  document.getElementById('lastUpdated').textContent = new Date().toLocaleDateString('en-IN', { day:'numeric', month:'short', year:'numeric' });

  // Init
  renderJobs();
</script>
</body>
</html>