<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Prosjektoversikt – Scaled CSM</title>
  <meta name="description" content="Oversiktlig prosjektsporingsverktøy for Scaled CSM – filtrer, sorter, oppdater og eksporter." />
  <link rel="stylesheet" href="./assets/styles.css" />
  <!-- React via CDN (no build needed) -->
  <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
  <!-- Babel Standalone to transpile JSX in the browser -->
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
</head>
<body>
  <header class="hero">
    <div class="container hero-inner">
      <div class="brand">
        <div class="brand-mark" aria-hidden="true">S</div>
        <div class="brand-text">
          <div class="brand-sub">Simployer</div>
          <h1 class="brand-title">Prosjektoversikt – Scaled CSM</h1>
        </div>
      </div>
      <p class="hero-desc">Hold oversikt over prosjekter, status, neste steg og risiko. Delbar og lett å oppdatere.</p>
      <div class="hero-actions">
        <button class="btn" id="btn-new">➕ Nytt prosjekt</button>
        <button class="btn btn-outline" id="btn-export">⤓ Eksporter CSV</button>
      </div>
    </div>
  </header>

  <main class="container content">
    <section class="card">
      <h2 class="card-title">Filtre</h2>
      <div class="filters">
        <label class="field">
          <span>Søk</span>
          <input id="filter-q" type="search" placeholder="Søk i prosjekt, kunde, mål, notater…" />
        </label>
        <label class="field">
          <span>Status</span>
          <select id="filter-status">
            <option value="alle">Alle</option>
            <option>Ikke startet</option>
            <option>Pågår</option>
            <option>På vent</option>
            <option>Fullført</option>
          </select>
        </label>
        <label class="field">
          <span>Eier</span>
          <input id="filter-owner" placeholder="Filtrer på eier (f.eks. Stine)" />
        </label>
        <div class="field counts" aria-live="polite">
          <div>Totalt: <strong id="count-total">0</strong></div>
          <div class="badge-row">
            <span class="badge" id="c-notstarted">Ikke startet: 0</span>
            <span class="badge badge-on">Pågår: 0</span>
            <span class="badge badge-wait">På vent: 0</span>
            <span class="badge badge-done">Fullført: 0</span>
          </div>
        </div>
      </div>
    </section>

    <section class="card">
      <h2 class="card-title">Prosjekter</h2>
      <div class="table-wrapper">
        <table class="table" id="table">
          <thead>
            <tr>
              <th><button class="th-sort" data-key="project">Prosjekt</button></th>
              <th><button class="th-sort" data-key="customer">Kunde / Segment</button></th>
              <th><button class="th-sort" data-key="startDate">Start</button></th>
              <th><button class="th-sort" data-key="deadline">Frist</button></th>
              <th><button class="th-sort" data-key="objective">Mål / leveranse</button></th>
              <th><button class="th-sort" data-key="owner">Eier</button></th>
              <th>Status</th>
              <th>Neste steg</th>
              <th>Risiko</th>
              <th>Notat</th>
              <th class="text-right">Handling</th>
            </tr>
          </thead>
          <tbody id="tbody"></tbody>
          <caption>Tips: bruk søk og statusfilter for rask rapportering i møter.</caption>
        </table>
      </div>
    </section>
  </main>

  <!-- Modal -->
  <div id="modal" class="modal hidden" role="dialog" aria-modal="true" aria-labelledby="modal-title">
    <div class="modal-card">
      <div class="modal-header">
        <h3 id="modal-title">Nytt prosjekt</h3>
      </div>
      <div class="modal-body">
        <div class="grid-2">
          <label class="field"><span>Prosjekt</span><input id="f-project" /></label>
          <label class="field"><span>Kunde</span><input id="f-customer" /></label>
          <label class="field"><span>Segment</span><input id="f-segment" placeholder="SMB / Mid-market / Enterprise" /></label>
          <label class="field"><span>Eier</span><input id="f-owner" value="Stine" /></label>
          <label class="field"><span>Startdato</span><input id="f-start" type="date" /></label>
          <label class="field"><span>Frist</span><input id="f-deadline" type="date" /></label>
          <label class="field col-2"><span>Mål / leveranse</span><input id="f-objective" /></label>
          <label class="field"><span>Status</span>
            <select id="f-status">
              <option>Ikke startet</option>
              <option selected>Pågår</option>
              <option>På vent</option>
              <option>Fullført</option>
            </select>
          </label>
          <label class="field col-2"><span>Neste steg</span><textarea id="f-next" rows="2"></textarea></label>
          <label class="field col-2"><span>Risiko / blokkere</span><textarea id="f-risk" rows="2"></textarea></label>
          <label class="field col-2"><span>Notater</span><textarea id="f-notes" rows="2"></textarea></label>
        </div>
      </div>
      <div class="modal-footer">
        <button class="btn btn-ghost" id="btn-cancel">Avbryt</button>
        <button class="btn" id="btn-save">Lagre</button>
      </div>
    </div>
  </div>

  <script type="text/babel" src="./assets/app.jsx"></script>
</body>
</html>
