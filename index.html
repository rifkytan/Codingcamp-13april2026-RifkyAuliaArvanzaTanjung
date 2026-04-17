<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Expense & Budget Visualizer</title>
  <link rel="stylesheet" href="css/style.css" />
  <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
</head>
<body>

<div class="app-wrapper">

  <!-- HEADER -->
  <header>
    <div class="header-title">
      <h1>Expense <span>&</span> Budget</h1>
      <p>VISUALIZER · RIFKY AULIA</p>
    </div>
    <button class="theme-toggle" id="themeToggle" title="Toggle tema">☀️</button>
  </header>

  <!-- BALANCE CARD -->
  <div class="balance-card">
    <div class="balance-label">TOTAL PENGELUARAN</div>
    <div class="balance-amount" id="balanceAmount">Rp 0</div>
    <div class="balance-stats">
      <div class="stat-item">
        <span class="stat-label">DIKELUARKAN</span>
        <span class="stat-value" id="statSpent">Rp 0</span>
      </div>
      <div class="stat-item">
        <span class="stat-label">TRANSAKSI</span>
        <span class="stat-value" id="statCount">0 tx</span>
      </div>
    </div>
  </div>

  <!-- TABS -->
  <div class="tabs">
    <button class="tab-btn active" data-tab="add">+ Tambah</button>
    <button class="tab-btn" data-tab="list">Riwayat</button>
    <button class="tab-btn" data-tab="chart">Grafik</button>
    <button class="tab-btn" data-tab="summary">Ringkasan</button>
  </div>

  <!-- PANEL: ADD -->
  <div class="panel active" id="panel-add">
    <div class="form-card">
      <h2>Tambah Transaksi</h2>

      <div class="form-group">
        <label for="itemName">Nama Item</label>
        <input type="text" id="itemName" placeholder="Contoh: Makan siang" />
        <div class="error-msg" id="nameError">⚠ Nama item wajib diisi</div>
      </div>

      <div class="form-row">
        <div class="form-group">
          <label for="itemAmount">Jumlah (Rp)</label>
          <input type="number" id="itemAmount" placeholder="0" min="1" />
          <div class="error-msg" id="amountError">⚠ Masukkan jumlah valid</div>
        </div>
        <div class="form-group">
          <label for="itemCategory">Kategori</label>
          <select id="itemCategory">
            <option value="">Pilih...</option>
            <option value="Food">Food</option>
            <option value="Transport">Transport</option>
            <option value="Fun">Fun</option>
          </select>
          <div class="error-msg" id="catError">⚠ Pilih kategori</div>
        </div>
      </div>

      <button class="btn-add" id="addBtn">Tambah Pengeluaran →</button>

      <!-- SPENDING LIMIT -->
      <div class="limit-section">
        <h3>🔔 Batas Pengeluaran</h3>
        <div class="limit-input-row">
          <input type="number" id="limitInput" placeholder="Masukkan batas (Rp)" min="0" />
          <button class="btn-set-limit" id="btnSetLimit">Simpan</button>
        </div>
        <div class="limit-alert" id="limitAlert"></div>
      </div>

      <!-- CUSTOM CATEGORY -->
      <div class="custom-cat-section">
        <h3>🏷 Kategori Kustom</h3>
        <div class="custom-cat-row">
          <input type="text" id="customCatInput" placeholder="Nama kategori baru..." />
          <button class="btn-add-cat" id="btnAddCat">+ Tambah</button>
        </div>
        <div class="custom-cats-list" id="customCatsList"></div>
      </div>
    </div>
  </div>

  <!-- PANEL: LIST -->
  <div class="panel" id="panel-list">
    <div class="list-header">
      <h2>Riwayat Transaksi</h2>
      <select class="sort-select" id="sortSelect">
        <option value="newest">Terbaru</option>
        <option value="oldest">Terlama</option>
        <option value="highest">Tertinggi</option>
        <option value="lowest">Terendah</option>
        <option value="category">Kategori</option>
      </select>
    </div>
    <div class="transaction-list" id="transactionList"></div>
  </div>

  <!-- PANEL: CHART -->
  <div class="panel" id="panel-chart">
    <div class="chart-card">
      <h2>Distribusi Pengeluaran</h2>
      <div class="chart-container">
        <canvas id="pieChart"></canvas>
        <div class="chart-empty" id="chartEmpty">
          Belum ada data untuk ditampilkan
        </div>
      </div>
      <div class="legend" id="chartLegend"></div>
    </div>
  </div>

  <!-- PANEL: SUMMARY -->
  <div class="panel" id="panel-summary">
    <div class="summary-month-header">
      <h2>Ringkasan Bulanan</h2>
      <div class="month-nav">
        <button class="btn-nav" id="btnPrevMonth">‹</button>
        <span class="month-label" id="monthLabel"></span>
        <button class="btn-nav" id="btnNextMonth">›</button>
      </div>
    </div>

    <div class="summary-cards">
      <div class="summary-card">
        <div class="summary-card-label">TOTAL KELUAR</div>
        <div class="summary-card-value" id="summaryTotal">Rp 0</div>
      </div>
      <div class="summary-card">
        <div class="summary-card-label">TRANSAKSI</div>
        <div class="summary-card-value" id="summaryCount">0</div>
      </div>
    </div>

    <div class="summary-by-cat">
      <h3>PER KATEGORI</h3>
      <div id="summaryByCat"></div>
    </div>
  </div>

</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script src="js/app.js"></script>
</body>
</html>
