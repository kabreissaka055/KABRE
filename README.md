# KABRE
Location de salle
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ImmoLoc — Maisons, Salles & Hébergements</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C9A84C;
    --gold-light: #F5E6C0;
    --dark: #1A1A2E;
    --dark-card: #16213E;
    --dark-surface: #0F3460;
    --text-primary: #F0EDE4;
    --text-muted: #A8A49A;
    --green: #2ECC71;
    --red: #E74C3C;
    --blue: #3498DB;
    --border: rgba(201,168,76,0.2);
    --radius: 16px;
    --shadow: 0 8px 32px rgba(0,0,0,0.4);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--dark);
    color: var(--text-primary);
    min-height: 100vh;
  }

  /* NAV */
  nav {
    position: sticky; top: 0; z-index: 100;
    background: rgba(26,26,46,0.95);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    padding: 0 2rem;
    display: flex; align-items: center; justify-content: space-between;
    height: 68px;
  }

  .logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 700;
    color: var(--gold);
    letter-spacing: -0.5px;
  }

  .logo span { color: var(--text-primary); }

  .nav-tabs {
    display: flex; gap: 4px;
    background: rgba(255,255,255,0.05);
    padding: 4px; border-radius: 10px;
  }

  .nav-tab {
    padding: 8px 20px; border-radius: 7px;
    border: none; cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem; font-weight: 500;
    background: transparent;
    color: var(--text-muted);
    transition: all 0.2s;
  }

  .nav-tab.active {
    background: var(--gold);
    color: var(--dark);
  }

  .nav-actions { display: flex; gap: 10px; }

  .btn-primary {
    background: var(--gold);
    color: var(--dark);
    border: none; cursor: pointer;
    padding: 9px 20px; border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem; font-weight: 500;
    transition: opacity 0.2s;
  }

  .btn-primary:hover { opacity: 0.85; }

  .btn-outline {
    background: transparent;
    color: var(--text-primary);
    border: 1px solid var(--border);
    cursor: pointer;
    padding: 9px 20px; border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem; font-weight: 400;
    transition: all 0.2s;
  }

  .btn-outline:hover { border-color: var(--gold); color: var(--gold); }

  /* HERO */
  .hero {
    background: linear-gradient(135deg, #0F3460 0%, #1A1A2E 50%, #16213E 100%);
    padding: 4rem 2rem 3rem;
    text-align: center;
    border-bottom: 1px solid var(--border);
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: rgba(201,168,76,0.15);
    border: 1px solid rgba(201,168,76,0.3);
    padding: 5px 14px; border-radius: 20px;
    font-size: 0.8rem; color: var(--gold);
    margin-bottom: 1.5rem;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 700; line-height: 1.2;
    margin-bottom: 1rem;
  }

  .hero h1 em { color: var(--gold); font-style: normal; }

  .hero p {
    color: var(--text-muted);
    font-size: 1rem; max-width: 560px;
    margin: 0 auto 2.5rem;
    line-height: 1.7;
  }

  .search-bar {
    display: flex; gap: 10px;
    max-width: 640px; margin: 0 auto;
    background: rgba(255,255,255,0.05);
    border: 1px solid var(--border);
    border-radius: 12px; padding: 8px;
  }

  .search-bar input, .search-bar select {
    background: transparent; border: none;
    color: var(--text-primary);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem; padding: 8px 12px;
    flex: 1; outline: none;
  }

  .search-bar select option { background: var(--dark-card); }

  .search-bar button {
    background: var(--gold); color: var(--dark);
    border: none; cursor: pointer;
    padding: 10px 24px; border-radius: 8px;
    font-weight: 500; font-size: 0.9rem;
    white-space: nowrap;
  }

  /* STATS */
  .stats {
    display: flex; justify-content: center; gap: 3rem;
    padding: 1.5rem 2rem;
    border-bottom: 1px solid var(--border);
    background: rgba(15,52,96,0.3);
  }

  .stat { text-align: center; }
  .stat-num { font-size: 1.5rem; font-weight: 600; color: var(--gold); }
  .stat-label { font-size: 0.75rem; color: var(--text-muted); margin-top: 2px; }

  /* MAIN LAYOUT */
  .main { display: flex; min-height: calc(100vh - 68px); }

  /* SIDEBAR */
  .sidebar {
    width: 280px; flex-shrink: 0;
    background: var(--dark-card);
    border-right: 1px solid var(--border);
    padding: 1.5rem;
    overflow-y: auto;
  }

  .sidebar-title {
    font-size: 0.75rem; font-weight: 500;
    color: var(--text-muted); letter-spacing: 0.08em;
    text-transform: uppercase; margin-bottom: 1rem;
  }

  .filter-group { margin-bottom: 1.5rem; }
  .filter-group label {
    display: block; font-size: 0.85rem;
    color: var(--text-muted); margin-bottom: 6px;
  }

  .filter-group select, .filter-group input {
    width: 100%; background: rgba(255,255,255,0.05);
    border: 1px solid var(--border); border-radius: 8px;
    color: var(--text-primary); padding: 8px 12px;
    font-family: 'DM Sans', sans-serif; font-size: 0.85rem;
    outline: none;
  }

  .filter-group select option { background: var(--dark-card); }

  .price-range { display: flex; gap: 8px; }
  .price-range input { flex: 1; }

  .filter-btn {
    width: 100%; background: var(--gold); color: var(--dark);
    border: none; cursor: pointer; padding: 10px;
    border-radius: 8px; font-weight: 500; font-size: 0.875rem;
    margin-top: 0.5rem;
  }

  /* CONTENT */
  .content { flex: 1; padding: 1.5rem; overflow-y: auto; }

  .content-header {
    display: flex; align-items: center; justify-content: space-between;
    margin-bottom: 1.5rem;
  }

  .results-count { font-size: 0.9rem; color: var(--text-muted); }
  .results-count strong { color: var(--text-primary); }

  .view-toggle { display: flex; gap: 4px; }

  .view-btn {
    background: rgba(255,255,255,0.05); border: 1px solid var(--border);
    color: var(--text-muted); cursor: pointer; padding: 6px 12px;
    border-radius: 6px; font-size: 1rem;
  }

  .view-btn.active { background: var(--gold); border-color: var(--gold); color: var(--dark); }

  /* CARDS GRID */
  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.25rem;
  }

  /* PROPERTY CARD */
  .card {
    background: var(--dark-card);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.2s, border-color 0.2s;
    position: relative;
  }

  .card:hover {
    transform: translateY(-3px);
    border-color: rgba(201,168,76,0.5);
  }

  .card-photos {
    position: relative; height: 200px;
    background: var(--dark-surface);
    overflow: hidden;
  }

  .card-photos img {
    width: 100%; height: 100%;
    object-fit: cover; display: block;
    transition: transform 0.3s;
  }

  .card:hover .card-photos img { transform: scale(1.04); }

  .photo-dots {
    position: absolute; bottom: 8px; left: 50%;
    transform: translateX(-50%);
    display: flex; gap: 4px;
  }

  .photo-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: rgba(255,255,255,0.5);
    cursor: pointer; transition: background 0.2s;
  }

  .photo-dot.active { background: white; }

  .photo-nav {
    position: absolute; top: 50%; transform: translateY(-50%);
    display: flex; justify-content: space-between;
    width: 100%; padding: 0 8px;
    opacity: 0; transition: opacity 0.2s;
  }

  .card:hover .photo-nav { opacity: 1; }

  .photo-arrow {
    background: rgba(0,0,0,0.6); color: white;
    border: none; cursor: pointer; padding: 4px 8px;
    border-radius: 6px; font-size: 0.9rem;
  }

  .card-badge {
    position: absolute; top: 10px; left: 10px;
    padding: 4px 10px; border-radius: 6px;
    font-size: 0.7rem; font-weight: 500;
    text-transform: uppercase; letter-spacing: 0.05em;
  }

  .badge-maison { background: rgba(46,204,113,0.85); color: #0a3d1a; }
  .badge-salle { background: rgba(52,152,219,0.85); color: #0a2a3d; }
  .badge-chambre { background: rgba(155,89,182,0.85); color: #2a0a3d; }

  .card-body { padding: 1rem 1.1rem 1.2rem; }

  .card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1rem; font-weight: 600;
    margin-bottom: 4px; line-height: 1.3;
  }

  .card-location {
    display: flex; align-items: center; gap: 5px;
    font-size: 0.8rem; color: var(--text-muted); margin-bottom: 10px;
  }

  .card-location svg { width: 12px; height: 12px; flex-shrink: 0; }

  .card-desc {
    font-size: 0.83rem; color: var(--text-muted);
    line-height: 1.5; margin-bottom: 12px;
    display: -webkit-box; -webkit-line-clamp: 2;
    -webkit-box-orient: vertical; overflow: hidden;
  }

  .card-tags { display: flex; flex-wrap: wrap; gap: 5px; margin-bottom: 12px; }

  .tag {
    background: rgba(255,255,255,0.06);
    border: 1px solid var(--border);
    padding: 3px 8px; border-radius: 5px;
    font-size: 0.72rem; color: var(--text-muted);
  }

  .card-footer {
    display: flex; align-items: center;
    justify-content: space-between;
    border-top: 1px solid var(--border); padding-top: 10px;
  }

  .card-price {
    font-size: 1.1rem; font-weight: 600; color: var(--gold);
  }

  .card-price span { font-size: 0.75rem; font-weight: 400; color: var(--text-muted); }

  .btn-voir {
    background: transparent; border: 1px solid var(--gold);
    color: var(--gold); padding: 6px 14px; border-radius: 7px;
    font-size: 0.8rem; cursor: pointer; transition: all 0.2s;
  }

  .btn-voir:hover { background: var(--gold); color: var(--dark); }

  /* MODAL */
  .modal-backdrop {
    position: fixed; inset: 0; z-index: 200;
    background: rgba(0,0,0,0.85);
    display: flex; align-items: center; justify-content: center;
    padding: 1rem; opacity: 0; pointer-events: none;
    transition: opacity 0.25s;
  }

  .modal-backdrop.open { opacity: 1; pointer-events: all; }

  .modal {
    background: var(--dark-card);
    border: 1px solid var(--border);
    border-radius: 20px;
    width: 100%; max-width: 820px;
    max-height: 90vh; overflow-y: auto;
    transform: translateY(20px); transition: transform 0.25s;
  }

  .modal-backdrop.open .modal { transform: translateY(0); }

  .modal-photos {
    position: relative; height: 340px;
    background: var(--dark-surface);
    border-radius: 20px 20px 0 0; overflow: hidden;
  }

  .modal-photos img {
    width: 100%; height: 100%; object-fit: cover;
  }

  .modal-photo-nav {
    position: absolute; top: 50%; transform: translateY(-50%);
    width: 100%; display: flex; justify-content: space-between; padding: 0 12px;
  }

  .modal-arrow {
    background: rgba(0,0,0,0.7); color: white;
    border: none; cursor: pointer;
    width: 40px; height: 40px; border-radius: 50%;
    font-size: 1.1rem; display: flex; align-items: center; justify-content: center;
  }

  .modal-photo-count {
    position: absolute; bottom: 12px; right: 12px;
    background: rgba(0,0,0,0.6); color: white;
    padding: 4px 10px; border-radius: 6px; font-size: 0.8rem;
  }

  .modal-close {
    position: absolute; top: 12px; right: 12px;
    background: rgba(0,0,0,0.7); color: white;
    border: none; cursor: pointer;
    width: 36px; height: 36px; border-radius: 50%;
    font-size: 1.2rem; display: flex; align-items: center; justify-content: center;
    z-index: 10;
  }

  .modal-body { padding: 1.5rem 2rem 2rem; }

  .modal-header {
    display: flex; justify-content: space-between;
    align-items: flex-start; margin-bottom: 1rem;
  }

  .modal-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem; font-weight: 600; line-height: 1.2;
  }

  .modal-price {
    font-size: 1.4rem; font-weight: 600; color: var(--gold);
    white-space: nowrap; margin-left: 1rem;
  }

  .modal-price small { font-size: 0.8rem; font-weight: 400; color: var(--text-muted); }

  .modal-meta {
    display: flex; flex-wrap: wrap; gap: 10px;
    margin-bottom: 1.2rem;
  }

  .meta-item {
    display: flex; align-items: center; gap: 6px;
    background: rgba(255,255,255,0.05);
    border: 1px solid var(--border);
    padding: 6px 12px; border-radius: 8px;
    font-size: 0.82rem; color: var(--text-muted);
  }

  .meta-item strong { color: var(--text-primary); }

  .modal-section { margin-bottom: 1.2rem; }

  .modal-section h3 {
    font-size: 0.8rem; font-weight: 500; letter-spacing: 0.06em;
    text-transform: uppercase; color: var(--gold);
    margin-bottom: 0.6rem;
  }

  .modal-section p {
    font-size: 0.9rem; color: var(--text-muted);
    line-height: 1.7;
  }

  .modal-contacts {
    background: rgba(201,168,76,0.08);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 12px; padding: 1rem 1.2rem;
  }

  .contact-row {
    display: flex; align-items: center; gap: 10px;
    padding: 8px 0;
    border-bottom: 1px solid var(--border);
  }

  .contact-row:last-child { border-bottom: none; }

  .contact-icon {
    width: 32px; height: 32px; border-radius: 8px;
    background: rgba(201,168,76,0.15);
    display: flex; align-items: center; justify-content: center;
    font-size: 0.9rem; flex-shrink: 0;
  }

  .contact-info { flex: 1; }
  .contact-label { font-size: 0.72rem; color: var(--text-muted); }
  .contact-value { font-size: 0.9rem; font-weight: 500; }

  .contact-action {
    background: var(--gold); color: var(--dark);
    border: none; cursor: pointer; padding: 6px 14px;
    border-radius: 7px; font-size: 0.8rem; font-weight: 500;
  }

  .map-placeholder {
    background: rgba(15,52,96,0.4);
    border: 1px solid var(--border);
    border-radius: 10px; height: 140px;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center; gap: 8px;
    color: var(--text-muted); font-size: 0.85rem;
    cursor: pointer;
  }

  .map-coords { font-size: 0.75rem; font-family: monospace; color: var(--gold); }

  /* FORM */
  .form-section {
    background: var(--dark-card);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.5rem; margin-bottom: 2rem;
  }

  .form-section h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem; margin-bottom: 1rem;
    color: var(--gold);
  }

  .form-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;
  }

  .form-group { margin-bottom: 0; }
  .form-group.full { grid-column: 1 / -1; }

  .form-group label {
    display: block; font-size: 0.82rem;
    color: var(--text-muted); margin-bottom: 5px;
  }

  .form-group input,
  .form-group select,
  .form-group textarea {
    width: 100%; background: rgba(255,255,255,0.05);
    border: 1px solid var(--border); border-radius: 8px;
    color: var(--text-primary); padding: 9px 12px;
    font-family: 'DM Sans', sans-serif; font-size: 0.875rem;
    outline: none; transition: border-color 0.2s;
  }

  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus {
    border-color: var(--gold);
  }

  .form-group select option { background: var(--dark-card); }
  .form-group textarea { resize: vertical; min-height: 80px; }

  .photo-upload-area {
    border: 2px dashed var(--border); border-radius: 10px;
    padding: 1.5rem; text-align: center; cursor: pointer;
    transition: border-color 0.2s; position: relative;
  }

  .photo-upload-area:hover { border-color: var(--gold); }

  .photo-upload-area input {
    position: absolute; inset: 0; opacity: 0; cursor: pointer;
    border: none; background: none; padding: 0;
  }

  .upload-icon { font-size: 2rem; margin-bottom: 8px; }
  .upload-text { font-size: 0.85rem; color: var(--text-muted); }
  .upload-text strong { color: var(--gold); }

  .photo-previews {
    display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px;
  }

  .photo-preview {
    width: 70px; height: 70px; border-radius: 8px;
    object-fit: cover; border: 1px solid var(--border);
  }

  .submit-btn {
    background: var(--gold); color: var(--dark);
    border: none; cursor: pointer; padding: 12px 32px;
    border-radius: 10px; font-family: 'DM Sans', sans-serif;
    font-size: 1rem; font-weight: 600; width: 100%;
    margin-top: 1rem; transition: opacity 0.2s;
  }

  .submit-btn:hover { opacity: 0.85; }

  /* TABS CONTENT */
  .tab-content { display: none; }
  .tab-content.active { display: block; }

  /* TOAST */
  .toast {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 300;
    background: var(--green); color: white;
    padding: 12px 20px; border-radius: 10px;
    font-size: 0.875rem; font-weight: 500;
    transform: translateY(100px); transition: transform 0.3s;
    box-shadow: 0 4px 20px rgba(0,0,0,0.3);
  }

  .toast.show { transform: translateY(0); }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    .main { flex-direction: column; }
    .sidebar { width: 100%; border-right: none; border-bottom: 1px solid var(--border); }
    .cards-grid { grid-template-columns: 1fr; }
    .form-grid { grid-template-columns: 1fr; }
    .modal-body { padding: 1rem 1.2rem 1.5rem; }
    nav { flex-wrap: wrap; height: auto; padding: 10px 1rem; gap: 8px; }
    .nav-tabs { order: 3; width: 100%; justify-content: center; }
    .stats { gap: 1.5rem; flex-wrap: wrap; }
    .hero { padding: 2rem 1rem; }
    .search-bar { flex-direction: column; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Immo<span>Loc</span></div>
  <div class="nav-tabs">
    <button class="nav-tab active" onclick="switchTab('annonces')">🏠 Annonces</button>
    <button class="nav-tab" onclick="switchTab('publier')">＋ Publier</button>
  </div>
  <div class="nav-actions">
    <button class="btn-outline">Connexion</button>
    <button class="btn-primary">Inscription</button>
  </div>
</nav>

<!-- HERO -->
<div id="hero-section">
  <div class="hero">
    <div class="hero-badge">🇧🇫 Burkina Faso — Immobilier & Événements</div>
    <h1>Trouvez votre <em>espace idéal</em><br>au Burkina Faso</h1>
    <p>Maisons à louer, salles d'événements et hébergements disponibles dans toutes les villes. Trouvez l'espace qui vous correspond.</p>
    <div class="search-bar">
      <select id="search-type" onchange="filterListings()">
        <option value="">Tous types</option>
        <option value="maison">Maison / Bureau</option>
        <option value="salle">Salle d'événement</option>
        <option value="chambre">Hébergement</option>
      </select>
      <input type="text" id="search-city" placeholder="Ville ou secteur..." oninput="filterListings()">
      <button onclick="filterListings()">Rechercher</button>
    </div>
  </div>
  <div class="stats">
    <div class="stat"><div class="stat-num" id="stat-maisons">0</div><div class="stat-label">Maisons & Bureaux</div></div>
    <div class="stat"><div class="stat-num" id="stat-salles">0</div><div class="stat-label">Salles d'événements</div></div>
    <div class="stat"><div class="stat-num" id="stat-chambres">0</div><div class="stat-label">Hébergements</div></div>
  </div>
</div>

<!-- TABS -->
<div id="tab-annonces" class="tab-content active">
  <div class="main">
    <!-- SIDEBAR -->
    <div class="sidebar">
      <div class="sidebar-title">Filtres</div>

      <div class="filter-group">
        <label>Type de bien</label>
        <select id="filter-type" onchange="filterListings()">
          <option value="">Tous</option>
          <option value="maison">Maison / Bureau</option>
          <option value="salle">Salle d'événement</option>
          <option value="chambre">Hébergement</option>
        </select>
      </div>

      <div class="filter-group">
        <label>Ville</label>
        <select id="filter-ville" onchange="filterListings()">
          <option value="">Toutes les villes</option>
          <option value="Ouagadougou">Ouagadougou</option>
          <option value="Bobo-Dioulasso">Bobo-Dioulasso</option>
          <option value="Koudougou">Koudougou</option>
          <option value="Banfora">Banfora</option>
          <option value="Ouahigouya">Ouahigouya</option>
        </select>
      </div>

      <div class="filter-group">
        <label>Budget max (FCFA/mois)</label>
        <input type="number" id="filter-prix" placeholder="Ex: 150000" oninput="filterListings()">
      </div>

      <button class="filter-btn" onclick="resetFilters()">Réinitialiser les filtres</button>
    </div>

    <!-- CONTENT -->
    <div class="content">
      <div class="content-header">
        <div class="results-count" id="results-count"><strong>0</strong> annonces trouvées</div>
        <div class="view-toggle">
          <button class="view-btn active">⊞</button>
          <button class="view-btn">☰</button>
        </div>
      </div>
      <div class="cards-grid" id="cards-grid"></div>
    </div>
  </div>
</div>

<!-- TAB PUBLIER -->
<div id="tab-publier" class="tab-content">
  <div style="max-width: 800px; margin: 2rem auto; padding: 0 1rem;">

    <div style="margin-bottom: 1.5rem;">
      <h2 style="font-family:'Playfair Display',serif; font-size:1.6rem; margin-bottom:6px;">Publier une annonce</h2>
      <p style="color:var(--text-muted); font-size:0.9rem;">Remplissez le formulaire ci-dessous pour mettre votre bien en location.</p>
    </div>

    <div class="form-section">
      <h2>Type d'annonce</h2>
      <div style="display:flex; gap:10px;">
        <button class="type-btn active" onclick="selectType('maison', this)" style="flex:1; padding:12px; border-radius:10px; border:2px solid var(--gold); background:rgba(201,168,76,0.1); color:var(--gold); cursor:pointer; font-family:'DM Sans',sans-serif; font-size:0.875rem;">🏠 Maison / Bureau</button>
        <button class="type-btn" onclick="selectType('salle', this)" style="flex:1; padding:12px; border-radius:10px; border:1px solid var(--border); background:transparent; color:var(--text-muted); cursor:pointer; font-family:'DM Sans',sans-serif; font-size:0.875rem;">🎉 Salle d'événement</button>
        <button class="type-btn" onclick="selectType('chambre', this)" style="flex:1; padding:12px; border-radius:10px; border:1px solid var(--border); background:transparent; color:var(--text-muted); cursor:pointer; font-family:'DM Sans',sans-serif; font-size:0.875rem;">🛏 Hébergement</button>
      </div>
    </div>

    <input type="hidden" id="form-type" value="maison">

    <!-- PHOTOS -->
    <div class="form-section">
      <h2>Photos (max. 5)</h2>
      <div class="photo-upload-area" onclick="document.getElementById('photo-input').click()">
        <input type="file" id="photo-input" accept="image/*" multiple onchange="handlePhotos(this)">
        <div class="upload-icon">📸</div>
        <div class="upload-text">Cliquez pour ajouter des photos<br><strong>Maximum 5 photos</strong></div>
      </div>
      <div class="photo-previews" id="photo-previews"></div>
    </div>

    <!-- INFOS GENERALES -->
    <div class="form-section">
      <h2>Informations générales</h2>
      <div class="form-grid">
        <div class="form-group full">
          <label>Titre de l'annonce *</label>
          <input type="text" id="f-titre" placeholder="Ex: Belle villa 4 chambres à Ouaga 2000">
        </div>
        <div class="form-group full">
          <label>Description *</label>
          <textarea id="f-description" placeholder="Décrivez le bien en détail : caractéristiques, équipements, avantages..."></textarea>
        </div>
        <div class="form-group">
          <label>Ville *</label>
          <select id="f-ville">
            <option value="">Sélectionner</option>
            <option>Ouagadougou</option>
            <option>Bobo-Dioulasso</option>
            <option>Koudougou</option>
            <option>Banfora</option>
            <option>Ouahigouya</option>
            <option>Autre</option>
          </select>
        </div>
        <div class="form-group">
          <label>Secteur / Quartier *</label>
          <input type="text" id="f-secteur" placeholder="Ex: Secteur 15, Ouaga 2000...">
        </div>
        <div class="form-group">
          <label>Latitude (géolocalisation)</label>
          <input type="text" id="f-lat" placeholder="Ex: 12.3641">
        </div>
        <div class="form-group">
          <label>Longitude (géolocalisation)</label>
          <input type="text" id="f-lng" placeholder="Ex: -1.5330">
        </div>
      </div>
    </div>

    <!-- CHAMPS SPÉCIFIQUES -->
    <div class="form-section" id="fields-maison">
      <h2>Détails — Maison / Bureau</h2>
      <div class="form-grid">
        <div class="form-group">
          <label>Loyer mensuel (FCFA) *</label>
          <input type="number" id="f-loyer" placeholder="Ex: 150000">
        </div>
        <div class="form-group">
          <label>Nombre de pièces</label>
          <input type="number" id="f-pieces" placeholder="Ex: 4">
        </div>
      </div>
    </div>

    <div class="form-section" id="fields-salle" style="display:none;">
      <h2>Détails — Salle d'événement</h2>
      <div class="form-grid">
        <div class="form-group">
          <label>Nom de la structure *</label>
          <input type="text" id="f-structure-salle" placeholder="Ex: Espace Karité">
        </div>
        <div class="form-group">
          <label>Capacité (nombre de places) *</label>
          <input type="number" id="f-capacite" placeholder="Ex: 300">
        </div>
        <div class="form-group">
          <label>Tarif de location (FCFA) *</label>
          <input type="number" id="f-tarif-salle" placeholder="Ex: 500000">
        </div>
        <div class="form-group">
          <label>Unité de tarification</label>
          <select id="f-unite-salle">
            <option value="par jour">Par jour</option>
            <option value="par soirée">Par soirée</option>
            <option value="par événement">Par événement</option>
            <option value="par heure">Par heure</option>
          </select>
        </div>
      </div>
    </div>

    <div class="form-section" id="fields-chambre" style="display:none;">
      <h2>Détails — Hébergement</h2>
      <div class="form-grid">
        <div class="form-group">
          <label>Nom de la structure *</label>
          <input type="text" id="f-structure-chambre" placeholder="Ex: Hôtel Le Palmier">
        </div>
        <div class="form-group">
          <label>Numéro(s) de réservation *</label>
          <input type="text" id="f-reservation" placeholder="Ex: +226 70 00 00 00 / booking.com/...">
        </div>
      </div>
    </div>

    <!-- CONTACTS -->
    <div class="form-section">
      <h2>Contacts du propriétaire / structure</h2>
      <div class="form-grid">
        <div class="form-group">
          <label>Nom complet *</label>
          <input type="text" id="f-nom" placeholder="Votre nom">
        </div>
        <div class="form-group">
          <label>Téléphone *</label>
          <input type="tel" id="f-tel" placeholder="+226 70 00 00 00">
        </div>
        <div class="form-group">
          <label>WhatsApp</label>
          <input type="tel" id="f-whatsapp" placeholder="+226 70 00 00 00">
        </div>
        <div class="form-group">
          <label>Email</label>
          <input type="email" id="f-email" placeholder="email@exemple.com">
        </div>
      </div>
    </div>

    <button class="submit-btn" onclick="submitForm()">✓ Publier l'annonce</button>
  </div>
</div>

<!-- MODAL -->
<div class="modal-backdrop" id="modal" onclick="closeModal(event)">
  <div class="modal" id="modal-inner">
    <div class="modal-photos">
      <button class="modal-close" onclick="closeModalDirect()">✕</button>
      <img id="modal-img" src="" alt="">
      <div class="modal-photo-nav">
        <button class="modal-arrow" onclick="modalNav(-1)">‹</button>
        <button class="modal-arrow" onclick="modalNav(1)">›</button>
      </div>
      <div class="modal-photo-count" id="modal-photo-count">1 / 1</div>
    </div>
    <div class="modal-body" id="modal-body"></div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">✓ Annonce publiée avec succès !</div>

<script>
// ============ DONNÉES EXEMPLE ============
let listings = [
  {
    id: 1, type: 'maison',
    titre: 'Belle villa moderne — 4 chambres',
    description: 'Magnifique villa de 4 chambres avec piscine, jardin et parking sécurisé. Idéale pour famille ou expatriés. Cuisine équipée, salon spacieux, 2 SDB. Gardien 24h/24.',
    ville: 'Ouagadougou', secteur: 'Ouaga 2000',
    lat: 12.3310, lng: -1.5024,
    prix: 450000, unite: 'par mois',
    tags: ['4 chambres', 'Piscine', 'Parking', 'Gardien'],
    contact: { nom: 'Konaté Issouf', tel: '+226 70 12 34 56', whatsapp: '+226 70 12 34 56', email: 'konate@mail.com' },
    photos: ['https://images.unsplash.com/photo-1564013799919-ab600027ffc6?w=800&q=80','https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=800&q=80','https://images.unsplash.com/photo-1484154218962-a197022b5858?w=800&q=80']
  },
  {
    id: 2, type: 'salle',
    titre: 'Espace Prestige — Salle de Réception',
    description: 'Grande salle climatisée de 500 places pour mariages, conférences, galas. Podium, sono professionnelle, éclairage LED. Espace VIP disponible. Parking 200 véhicules.',
    ville: 'Ouagadougou', secteur: 'Secteur 15',
    lat: 12.3641, lng: -1.5330,
    prix: 800000, unite: 'par événement',
    structure: 'Centre Prestige Évènements',
    capacite: 500,
    tags: ['500 places', 'Climatisé', 'Sono', 'Parking'],
    contact: { nom: 'Diallo Fatoumata', tel: '+226 76 98 76 54', whatsapp: '+226 76 98 76 54', email: 'prestige@events.bf' },
    photos: ['https://images.unsplash.com/photo-1519167758481-83f550bb49b3?w=800&q=80','https://images.unsplash.com/photo-1464366400600-7168b8af9bc3?w=800&q=80','https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=800&q=80']
  },
  {
    id: 3, type: 'chambre',
    titre: 'Hôtel Le Baobab — Hébergement de qualité',
    description: 'Hôtel 3 étoiles au cœur de Ouagadougou. Chambres climatisées, WiFi haut débit, restaurant, salle de sport. Service de navette aéroport disponible.',
    ville: 'Ouagadougou', secteur: 'Centre-ville',
    lat: 12.3714, lng: -1.5255,
    prix: 35000, unite: 'par nuit',
    structure: 'Hôtel Le Baobab',
    reservation: '+226 25 31 00 00 / baobab-hotel.bf',
    tags: ['3 étoiles', 'WiFi', 'Restaurant', 'Navette'],
    contact: { nom: 'Réception', tel: '+226 25 31 00 00', whatsapp: '+226 70 31 00 01', email: 'info@baobab.bf' },
    photos: ['https://images.unsplash.com/photo-1631049307264-da0ec9d70304?w=800&q=80','https://images.unsplash.com/photo-1611892440504-42a792e24d32?w=800&q=80','https://images.unsplash.com/photo-1578683010236-d716f9a3f461?w=800&q=80']
  },
  {
    id: 4, type: 'maison',
    titre: 'Appartement F3 — Zone industrielle',
    description: 'Appartement fonctionnel de 3 pièces pour professionnels ou couple. Quartier calme et sécurisé. Eau et électricité disponibles. À 5 min du centre commercial.',
    ville: 'Bobo-Dioulasso', secteur: 'Zone industrielle',
    lat: 11.1771, lng: -4.2979,
    prix: 120000, unite: 'par mois',
    tags: ['3 pièces', 'Calme', 'Sécurisé', 'Centre commercial'],
    contact: { nom: 'Traoré Mamadou', tel: '+226 71 45 67 89', whatsapp: '', email: '' },
    photos: ['https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?w=800&q=80','https://images.unsplash.com/photo-1502672260266-1c1ef2d93688?w=800&q=80']
  },
  {
    id: 5, type: 'salle',
    titre: 'Espace Horizon — Salle Modulable',
    description: 'Salle polyvalente de 200 places. Configuration théâtre, cocktail ou banquet. Cuisine équipée, terrasse couverte. Idéale pour séminaires, anniversaires ou cérémonies.',
    ville: 'Bobo-Dioulasso', secteur: 'Secteur 22',
    lat: 11.1833, lng: -4.2985,
    prix: 350000, unite: 'par jour',
    structure: 'Espace Horizon',
    capacite: 200,
    tags: ['200 places', 'Modulable', 'Terrasse', 'Cuisine'],
    contact: { nom: 'Sawadogo Alice', tel: '+226 77 22 33 44', whatsapp: '+226 77 22 33 44', email: 'horizon@events.bf' },
    photos: ['https://images.unsplash.com/photo-1497366216548-37526070297c?w=800&q=80','https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=800&q=80']
  },
  {
    id: 6, type: 'chambre',
    titre: 'Résidence Amitié — Chambres Meublées',
    description: 'Résidence calme proposant des chambres meublées climatisées pour séjours court ou long terme. Sécurité 24h, connexion WiFi, petit déjeuner inclus. Idéal pour voyageurs d\'affaires.',
    ville: 'Koudougou', secteur: 'Centre',
    lat: 12.2500, lng: -2.3628,
    prix: 18000, unite: 'par nuit',
    structure: 'Résidence Amitié',
    reservation: '+226 70 55 44 33',
    tags: ['Meublé', 'Climatisé', 'WiFi', 'Petit déj.'],
    contact: { nom: 'Ouédraogo Pierre', tel: '+226 70 55 44 33', whatsapp: '+226 70 55 44 33', email: '' },
    photos: ['https://images.unsplash.com/photo-1566665797739-1674de7a421a?w=800&q=80','https://images.unsplash.com/photo-1582719508461-905c673771fd?w=800&q=80']
  }
];

let currentModal = null;
let modalPhotoIndex = 0;

// ============ STATS ============
function updateStats() {
  document.getElementById('stat-maisons').textContent = listings.filter(l=>l.type==='maison').length;
  document.getElementById('stat-salles').textContent = listings.filter(l=>l.type==='salle').length;
  document.getElementById('stat-chambres').textContent = listings.filter(l=>l.type==='chambre').length;
}

// ============ RENDER CARDS ============
function renderCards(data) {
  const grid = document.getElementById('cards-grid');
  document.getElementById('results-count').innerHTML = `<strong>${data.length}</strong> annonce${data.length>1?'s':''} trouvée${data.length>1?'s':''}`;

  if(data.length === 0) {
    grid.innerHTML = `<div style="grid-column:1/-1; text-align:center; padding:3rem; color:var(--text-muted);">
      <div style="font-size:2rem; margin-bottom:1rem;">🔍</div>
      <p>Aucune annonce trouvée pour ces critères.</p>
    </div>`;
    return;
  }

  grid.innerHTML = data.map((l, idx) => {
    const badgeClass = l.type==='maison'?'badge-maison':l.type==='salle'?'badge-salle':'badge-chambre';
    const badgeText = l.type==='maison'?'Maison/Bureau':l.type==='salle'?'Salle':'Hébergement';
    const dots = l.photos.map((_, i) => `<div class="photo-dot${i===0?' active':''}" onclick="event.stopPropagation();cardPhoto(${l.id},${i})"></div>`).join('');
    const tags = l.tags.slice(0,3).map(t=>`<span class="tag">${t}</span>`).join('');

    return `<div class="card" onclick="openModal(${l.id})">
      <div class="card-photos" id="card-photos-${l.id}">
        <img src="${l.photos[0]}" alt="${l.titre}" id="card-img-${l.id}" loading="lazy">
        <div class="photo-nav">
          <button class="photo-arrow" onclick="event.stopPropagation();cardNav(${l.id},-1)">‹</button>
          <button class="photo-arrow" onclick="event.stopPropagation();cardNav(${l.id},1)">›</button>
        </div>
        <div class="photo-dots">${dots}</div>
        <div class="card-badge ${badgeClass}">${badgeText}</div>
      </div>
      <div class="card-body">
        <div class="card-title">${l.titre}</div>
        <div class="card-location">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
          ${l.ville} — ${l.secteur}
        </div>
        <div class="card-desc">${l.description}</div>
        <div class="card-tags">${tags}</div>
        <div class="card-footer">
          <div class="card-price">${l.prix.toLocaleString('fr-FR')} FCFA <span>/ ${l.unite||'mois'}</span></div>
          <button class="btn-voir">Voir →</button>
        </div>
      </div>
    </div>`;
  }).join('');

  // Track photo indices per card
  data.forEach(l => { window['card_idx_'+l.id] = 0; });
}

const cardIdxMap = {};

function cardNav(id, dir) {
  const l = listings.find(x=>x.id===id);
  if(!l) return;
  if(!(id in cardIdxMap)) cardIdxMap[id] = 0;
  cardIdxMap[id] = (cardIdxMap[id] + dir + l.photos.length) % l.photos.length;
  document.getElementById('card-img-'+id).src = l.photos[cardIdxMap[id]];
  document.querySelectorAll(`#card-photos-${id} .photo-dot`).forEach((d,i)=>d.classList.toggle('active', i===cardIdxMap[id]));
}

function cardPhoto(id, idx) {
  const l = listings.find(x=>x.id===id);
  if(!l) return;
  cardIdxMap[id] = idx;
  document.getElementById('card-img-'+id).src = l.photos[idx];
  document.querySelectorAll(`#card-photos-${id} .photo-dot`).forEach((d,i)=>d.classList.toggle('active', i===idx));
}

// ============ FILTER ============
function filterListings() {
  const type = document.getElementById('filter-type').value || document.getElementById('search-type').value;
  const ville = document.getElementById('filter-ville').value;
  const prix = parseInt(document.getElementById('filter-prix').value) || Infinity;
  const search = document.getElementById('search-city').value.toLowerCase();

  const filtered = listings.filter(l => {
    if(type && l.type !== type) return false;
    if(ville && l.ville !== ville) return false;
    if(l.prix > prix) return false;
    if(search && !l.ville.toLowerCase().includes(search) && !l.secteur.toLowerCase().includes(search) && !l.titre.toLowerCase().includes(search)) return false;
    return true;
  });
  renderCards(filtered);
}

function resetFilters() {
  document.getElementById('filter-type').value = '';
  document.getElementById('filter-ville').value = '';
  document.getElementById('filter-prix').value = '';
  document.getElementById('search-city').value = '';
  document.getElementById('search-type').value = '';
  filterListings();
}

// ============ MODAL ============
function openModal(id) {
  const l = listings.find(x=>x.id===id);
  if(!l) return;
  currentModal = l;
  modalPhotoIndex = 0;
  document.getElementById('modal-img').src = l.photos[0];
  document.getElementById('modal-photo-count').textContent = `1 / ${l.photos.length}`;

  let specific = '';
  if(l.type === 'maison') {
    specific = `<div class="modal-section">
      <h3>Loyer</h3>
      <p style="font-size:1.5rem; font-weight:600; color:var(--gold);">${l.prix.toLocaleString('fr-FR')} FCFA <span style="font-size:0.85rem; font-weight:400; color:var(--text-muted);">/ mois</span></p>
    </div>`;
  } else if(l.type === 'salle') {
    specific = `<div class="modal-section">
      <h3>Structure</h3>
      <p>${l.structure}</p>
    </div>
    <div class="modal-section">
      <h3>Capacité & Tarifs</h3>
      <p>Jusqu'à <strong style="color:var(--text-primary);">${l.capacite} places</strong> — <strong style="color:var(--gold);">${l.prix.toLocaleString('fr-FR')} FCFA</strong> ${l.unite}</p>
    </div>`;
  } else {
    specific = `<div class="modal-section">
      <h3>Structure</h3>
      <p>${l.structure}</p>
    </div>
    <div class="modal-section">
      <h3>Réservation</h3>
      <p style="color:var(--gold);">${l.reservation}</p>
    </div>
    <div class="modal-section">
      <h3>Tarif</h3>
      <p style="font-size:1.2rem; font-weight:600; color:var(--gold);">${l.prix.toLocaleString('fr-FR')} FCFA <span style="font-size:0.8rem; font-weight:400; color:var(--text-muted);">/ ${l.unite}</span></p>
    </div>`;
  }

  const tags = l.tags.map(t=>`<span class="tag">${t}</span>`).join('');
  const badgeText = l.type==='maison'?'Maison / Bureau':l.type==='salle'?'Salle d\'événement':'Hébergement';

  document.getElementById('modal-body').innerHTML = `
    <div class="modal-header">
      <div>
        <div style="margin-bottom:6px;"><span style="background:rgba(201,168,76,0.15);border:1px solid rgba(201,168,76,0.3);padding:3px 10px;border-radius:5px;font-size:0.72rem;color:var(--gold);">${badgeText}</span></div>
        <div class="modal-title">${l.titre}</div>
      </div>
    </div>

    <div class="modal-meta">
      <div class="meta-item">📍 <strong>${l.ville}</strong> — ${l.secteur}</div>
      ${l.capacite ? `<div class="meta-item">👥 <strong>${l.capacite} places</strong></div>` : ''}
      ${l.photos.length > 1 ? `<div class="meta-item">📸 <strong>${l.photos.length} photos</strong></div>` : ''}
    </div>

    <div class="modal-section">
      <h3>Description</h3>
      <p>${l.description}</p>
    </div>

    <div class="modal-section">
      <h3>Équipements & caractéristiques</h3>
      <div class="card-tags">${tags}</div>
    </div>

    ${specific}

    <div class="modal-section">
      <h3>Contacts</h3>
      <div class="modal-contacts">
        <div class="contact-row">
          <div class="contact-icon">👤</div>
          <div class="contact-info">
            <div class="contact-label">Propriétaire / Contact</div>
            <div class="contact-value">${l.contact.nom}</div>
          </div>
        </div>
        <div class="contact-row">
          <div class="contact-icon">📞</div>
          <div class="contact-info">
            <div class="contact-label">Téléphone</div>
            <div class="contact-value">${l.contact.tel}</div>
          </div>
          <a href="tel:${l.contact.tel}"><button class="contact-action">Appeler</button></a>
        </div>
        ${l.contact.whatsapp ? `<div class="contact-row">
          <div class="contact-icon">💬</div>
          <div class="contact-info">
            <div class="contact-label">WhatsApp</div>
            <div class="contact-value">${l.contact.whatsapp}</div>
          </div>
          <a href="https://wa.me/${l.contact.whatsapp.replace(/\s+/g,'').replace('+','')}" target="_blank"><button class="contact-action" style="background:#25D366;">WhatsApp</button></a>
        </div>` : ''}
        ${l.contact.email ? `<div class="contact-row">
          <div class="contact-icon">✉️</div>
          <div class="contact-info">
            <div class="contact-label">Email</div>
            <div class="contact-value">${l.contact.email}</div>
          </div>
          <a href="mailto:${l.contact.email}"><button class="contact-action">Email</button></a>
        </div>` : ''}
      </div>
    </div>

    <div class="modal-section">
      <h3>Géolocalisation</h3>
      <div class="map-placeholder" onclick="openMaps(${l.lat},${l.lng})">
        <div style="font-size:2rem;">🗺️</div>
        <div>Voir sur Google Maps</div>
        <div class="map-coords">${l.lat}, ${l.lng}</div>
        <div style="font-size:0.72rem; margin-top:4px; color:var(--text-muted);">Cliquer pour ouvrir</div>
      </div>
    </div>
  `;

  document.getElementById('modal').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function openMaps(lat, lng) {
  window.open(`https://www.google.com/maps?q=${lat},${lng}`, '_blank');
}

function modalNav(dir) {
  if(!currentModal) return;
  modalPhotoIndex = (modalPhotoIndex + dir + currentModal.photos.length) % currentModal.photos.length;
  document.getElementById('modal-img').src = currentModal.photos[modalPhotoIndex];
  document.getElementById('modal-photo-count').textContent = `${modalPhotoIndex+1} / ${currentModal.photos.length}`;
}

function closeModal(e) {
  if(e.target === document.getElementById('modal')) closeModalDirect();
}

function closeModalDirect() {
  document.getElementById('modal').classList.remove('open');
  document.body.style.overflow = '';
  currentModal = null;
}

// ============ TABS ============
function switchTab(tab) {
  document.querySelectorAll('.tab-content').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t=>t.classList.remove('active'));
  document.getElementById('tab-'+tab).classList.add('active');
  event.target.classList.add('active');
  document.getElementById('hero-section').style.display = tab==='annonces'?'':'none';
}

// ============ FORM TYPE SELECT ============
function selectType(type, btn) {
  document.querySelectorAll('.type-btn').forEach(b=>{
    b.style.border = '1px solid var(--border)';
    b.style.background = 'transparent';
    b.style.color = 'var(--text-muted)';
  });
  btn.style.border = '2px solid var(--gold)';
  btn.style.background = 'rgba(201,168,76,0.1)';
  btn.style.color = 'var(--gold)';
  document.getElementById('form-type').value = type;
  document.getElementById('fields-maison').style.display = type==='maison'?'':'none';
  document.getElementById('fields-salle').style.display = type==='salle'?'':'none';
  document.getElementById('fields-chambre').style.display = type==='chambre'?'':'none';
}

// ============ PHOTO UPLOAD ============
let uploadedPhotos = [];
function handlePhotos(input) {
  const files = Array.from(input.files).slice(0, 5);
  uploadedPhotos = files;
  const preview = document.getElementById('photo-previews');
  preview.innerHTML = '';
  files.forEach(f => {
    const reader = new FileReader();
    reader.onload = e => {
      const img = document.createElement('img');
      img.className = 'photo-preview';
      img.src = e.target.result;
      preview.appendChild(img);
    };
    reader.readAsDataURL(f);
  });
}

// ============ FORM SUBMIT ============
function submitForm() {
  const type = document.getElementById('form-type').value;
  const titre = document.getElementById('f-titre').value.trim();
  const ville = document.getElementById('f-ville').value;
  const nom = document.getElementById('f-nom').value.trim();
  const tel = document.getElementById('f-tel').value.trim();

  if(!titre || !ville || !nom || !tel) {
    alert('Veuillez remplir tous les champs obligatoires (*).');
    return;
  }

  const newListing = {
    id: Date.now(),
    type, titre,
    description: document.getElementById('f-description').value,
    ville, secteur: document.getElementById('f-secteur').value,
    lat: parseFloat(document.getElementById('f-lat').value) || 12.3641,
    lng: parseFloat(document.getElementById('f-lng').value) || -1.5330,
    tags: [],
    contact: {
      nom, tel,
      whatsapp: document.getElementById('f-whatsapp').value,
      email: document.getElementById('f-email').value
    },
    photos: uploadedPhotos.length > 0
      ? uploadedPhotos.map((f,i) => URL.createObjectURL(f))
      : ['https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=800&q=80']
  };

  if(type === 'maison') {
    newListing.prix = parseInt(document.getElementById('f-loyer').value) || 0;
    newListing.unite = 'mois';
  } else if(type === 'salle') {
    newListing.prix = parseInt(document.getElementById('f-tarif-salle').value) || 0;
    newListing.unite = document.getElementById('f-unite-salle').value;
    newListing.structure = document.getElementById('f-structure-salle').value;
    newListing.capacite = parseInt(document.getElementById('f-capacite').value) || 0;
  } else {
    newListing.prix = 0; newListing.unite = 'nuit';
    newListing.structure = document.getElementById('f-structure-chambre').value;
    newListing.reservation = document.getElementById('f-reservation').value;
  }

  listings.push(newListing);
  updateStats();

  const toast = document.getElementById('toast');
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 3500);

  switchTab('annonces');
  document.querySelector('.nav-tab').click();
  filterListings();
}

// ============ INIT ============
updateStats();
filterListings();
</script>
</body>
</html>
