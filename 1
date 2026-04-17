// =============================================
//  EXPENSE & BUDGET VISUALIZER
//  CodingCamp-13april2026-RifkyAuliaArvanzaTanjung
// =============================================

const STORAGE_KEY = 'rifky_expenses';
const SETTINGS_KEY = 'rifky_settings';

// Default categories
const DEFAULT_CATEGORIES = ['Food', 'Transport', 'Fun'];
const CAT_COLORS = {
  Food: '#ff6b6b',
  Transport: '#4d96ff',
  Fun: '#ffd93d',
};
const CUSTOM_COLOR = '#c77dff';

// ---- STATE ----
let transactions = [];
let settings = {
  spendingLimit: 0,
  customCategories: [],
  theme: 'dark',
};
let currentSort = 'newest';
let currentMonth = new Date().getMonth();
let currentYear = new Date().getFullYear();
let pieChart = null;

// ---- INIT ----
function init() {
  loadData();
  applyTheme();
  renderAll();
  setupEventListeners();
}

// ---- STORAGE ----
function loadData() {
  try {
    const txData = localStorage.getItem(STORAGE_KEY);
    const settingsData = localStorage.getItem(SETTINGS_KEY);
    transactions = txData ? JSON.parse(txData) : [];
    settings = settingsData ? { ...settings, ...JSON.parse(settingsData) } : settings;
  } catch (e) {
    transactions = [];
  }
}

function saveData() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(transactions));
  localStorage.setItem(SETTINGS_KEY, JSON.stringify(settings));
}

// ---- THEME ----
function applyTheme() {
  document.documentElement.setAttribute('data-theme', settings.theme);
  document.getElementById('themeToggle').textContent = settings.theme === 'dark' ? '☀️' : '🌙';
}

// ---- ALL CATEGORIES ----
function getAllCategories() {
  return [...DEFAULT_CATEGORIES, ...settings.customCategories];
}

function getCatColor(cat) {
  return CAT_COLORS[cat] || CUSTOM_COLOR;
}

// ---- FORMAT ----
function formatRp(num) {
  return 'Rp ' + Math.abs(num).toLocaleString('id-ID');
}

function formatDate(iso) {
  const d = new Date(iso);
  return d.toLocaleDateString('id-ID', { day: '2-digit', month: 'short' });
}

function getMonthName(m, y) {
  return new Date(y, m, 1).toLocaleDateString('id-ID', { month: 'long', year: 'numeric' });
}

// ---- RENDER ALL ----
function renderAll() {
  renderBalance();
  renderTransactionList();
  renderChart();
  renderSummary();
  renderCategorySelect();
  renderCustomCatChips();
  renderLimitStatus();
}

// ---- BALANCE ----
function renderBalance() {
  const total = transactions.reduce((s, t) => s - t.amount, 0);
  const totalSpent = transactions.reduce((s, t) => s + t.amount, 0);
  const count = transactions.length;

  const el = document.getElementById('balanceAmount');
  el.textContent = formatRp(totalSpent);
  el.className = 'balance-amount';

  document.getElementById('statSpent').textContent = formatRp(totalSpent);
  document.getElementById('statCount').textContent = count + ' tx';
}

// ---- TRANSACTION LIST ----
function getSortedTransactions() {
  const list = [...transactions];
  switch (currentSort) {
    case 'newest': return list.sort((a, b) => new Date(b.date) - new Date(a.date));
    case 'oldest': return list.sort((a, b) => new Date(a.date) - new Date(b.date));
    case 'highest': return list.sort((a, b) => b.amount - a.amount);
    case 'lowest': return list.sort((a, b) => a.amount - b.amount);
    case 'category': return list.sort((a, b) => a.category.localeCompare(b.category));
    default: return list;
  }
}

function renderTransactionList() {
  const container = document.getElementById('transactionList');
  const sorted = getSortedTransactions();

  if (sorted.length === 0) {
    container.innerHTML = `
      <div class="empty-state">
        <div class="empty-icon">💸</div>
        <p>Belum ada transaksi.<br>Tambahkan pengeluaran pertamamu!</p>
      </div>`;
    return;
  }

  container.innerHTML = sorted.map(tx => `
    <div class="transaction-item" data-id="${tx.id}">
      <div class="tx-cat-dot" style="background:${getCatColor(tx.category)}"></div>
      <div class="tx-info">
        <div class="tx-name">${escapeHtml(tx.name)}</div>
        <div class="tx-meta">
          <span class="tx-category" style="color:${getCatColor(tx.category)}">${tx.category}</span>
          <span class="tx-date">${formatDate(tx.date)}</span>
        </div>
      </div>
      <div class="tx-amount" style="color:${getCatColor(tx.category)}">${formatRp(tx.amount)}</div>
      <button class="btn-delete" onclick="deleteTransaction('${tx.id}')" title="Hapus">✕</button>
    </div>
  `).join('');
}

// ---- ADD TRANSACTION ----
function addTransaction() {
  const nameEl = document.getElementById('itemName');
  const amountEl = document.getElementById('itemAmount');
  const catEl = document.getElementById('itemCategory');

  const nameErr = document.getElementById('nameError');
  const amountErr = document.getElementById('amountError');
  const catErr = document.getElementById('catError');

  // Reset errors
  [nameEl, amountEl, catEl].forEach(el => el.classList.remove('input-error'));
  [nameErr, amountErr, catErr].forEach(el => el.style.display = 'none');

  let valid = true;

  if (!nameEl.value.trim()) {
    nameEl.classList.add('input-error');
    nameErr.style.display = 'block';
    valid = false;
  }

  const amount = parseFloat(amountEl.value);
  if (!amountEl.value || isNaN(amount) || amount <= 0) {
    amountEl.classList.add('input-error');
    amountErr.style.display = 'block';
    valid = false;
  }

  if (!catEl.value) {
    catEl.classList.add('input-error');
    catErr.style.display = 'block';
    valid = false;
  }

  if (!valid) return;

  const tx = {
    id: Date.now().toString(),
    name: nameEl.value.trim(),
    amount: amount,
    category: catEl.value,
    date: new Date().toISOString(),
  };

  transactions.unshift(tx);
  saveData();
  renderAll();

  nameEl.value = '';
  amountEl.value = '';
  catEl.value = '';

  showToast('Transaksi ditambahkan! 🎉');
}

// ---- DELETE ----
function deleteTransaction(id) {
  transactions = transactions.filter(t => t.id !== id);
  saveData();
  renderAll();
  showToast('Transaksi dihapus.');
}

// ---- CHART ----
function renderChart() {
  const canvas = document.getElementById('pieChart');
  const emptyEl = document.getElementById('chartEmpty');
  const legendEl = document.getElementById('chartLegend');

  if (transactions.length === 0) {
    canvas.style.display = 'none';
    emptyEl.style.display = 'block';
    legendEl.innerHTML = '';
    if (pieChart) { pieChart.destroy(); pieChart = null; }
    return;
  }

  canvas.style.display = 'block';
  emptyEl.style.display = 'none';

  // Aggregate by category
  const catTotals = {};
  transactions.forEach(tx => {
    catTotals[tx.category] = (catTotals[tx.category] || 0) + tx.amount;
  });

  const labels = Object.keys(catTotals);
  const values = labels.map(l => catTotals[l]);
  const colors = labels.map(l => getCatColor(l));
  const total = values.reduce((s, v) => s + v, 0);

  if (pieChart) pieChart.destroy();

  pieChart = new Chart(canvas, {
    type: 'doughnut',
    data: {
      labels,
      datasets: [{
        data: values,
        backgroundColor: colors,
        borderWidth: 2,
        borderColor: getComputedStyle(document.documentElement).getPropertyValue('--surface').trim() || '#1a1825',
        hoverOffset: 8,
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      cutout: '65%',
      plugins: {
        legend: { display: false },
        tooltip: {
          callbacks: {
            label: ctx => ` ${formatRp(ctx.raw)} (${((ctx.raw / total) * 100).toFixed(1)}%)`
          }
        }
      }
    }
  });

  // Render legend
  legendEl.innerHTML = labels.map((label, i) => `
    <div class="legend-item">
      <div class="legend-dot" style="background:${colors[i]}"></div>
      <span class="legend-name">${label}</span>
      <span class="legend-amount">${formatRp(values[i])}</span>
      <span class="legend-pct">${((values[i] / total) * 100).toFixed(0)}%</span>
    </div>
  `).join('');
}

// ---- SUMMARY ----
function renderSummary() {
  const label = document.getElementById('monthLabel');
  label.textContent = getMonthName(currentMonth, currentYear);

  const monthTx = transactions.filter(tx => {
    const d = new Date(tx.date);
    return d.getMonth() === currentMonth && d.getFullYear() === currentYear;
  });

  const total = monthTx.reduce((s, t) => s + t.amount, 0);
  const count = monthTx.length;

  document.getElementById('summaryTotal').textContent = formatRp(total);
  document.getElementById('summaryCount').textContent = count;

  // By category
  const catTotals = {};
  monthTx.forEach(tx => {
    catTotals[tx.category] = (catTotals[tx.category] || 0) + tx.amount;
  });

  const byCatEl = document.getElementById('summaryByCat');
  if (Object.keys(catTotals).length === 0) {
    byCatEl.innerHTML = '<p style="color:var(--text-muted);font-size:13px;opacity:0.6">Tidak ada transaksi bulan ini.</p>';
    return;
  }

  const sortedCats = Object.entries(catTotals).sort((a, b) => b[1] - a[1]);
  const maxAmt = sortedCats[0][1];

  byCatEl.innerHTML = sortedCats.map(([cat, amt]) => `
    <div class="cat-bar-item">
      <div class="cat-bar-header">
        <span class="cat-bar-name" style="color:${getCatColor(cat)}">${cat}</span>
        <span class="cat-bar-amt">${formatRp(amt)}</span>
      </div>
      <div class="cat-bar-track">
        <div class="cat-bar-fill" style="width:${(amt/maxAmt*100).toFixed(1)}%;background:${getCatColor(cat)}"></div>
      </div>
    </div>
  `).join('');
}

// ---- CATEGORY SELECT ----
function renderCategorySelect() {
  const sel = document.getElementById('itemCategory');
  const current = sel.value;
  const cats = getAllCategories();

  sel.innerHTML = '<option value="">Pilih kategori...</option>' +
    cats.map(c => `<option value="${c}" ${c === current ? 'selected' : ''}>${c}</option>`).join('');
}

// ---- CUSTOM CATEGORIES ----
function addCustomCategory() {
  const input = document.getElementById('customCatInput');
  const name = input.value.trim();
  if (!name) return;
  if (getAllCategories().map(c => c.toLowerCase()).includes(name.toLowerCase())) {
    showToast('Kategori sudah ada!');
    return;
  }
  settings.customCategories.push(name);
  saveData();
  renderCategorySelect();
  renderCustomCatChips();
  input.value = '';
  showToast(`Kategori "${name}" ditambahkan!`);
}

function removeCustomCategory(name) {
  settings.customCategories = settings.customCategories.filter(c => c !== name);
  saveData();
  renderCategorySelect();
  renderCustomCatChips();
}

function renderCustomCatChips() {
  const el = document.getElementById('customCatsList');
  if (settings.customCategories.length === 0) {
    el.innerHTML = '';
    return;
  }
  el.innerHTML = settings.customCategories.map(c => `
    <div class="cat-chip">
      <span>${escapeHtml(c)}</span>
      <button class="cat-chip-del" onclick="removeCustomCategory('${escapeHtml(c)}')">✕</button>
    </div>
  `).join('');
}

// ---- SPENDING LIMIT ----
function setSpendingLimit() {
  const val = parseFloat(document.getElementById('limitInput').value);
  if (isNaN(val) || val < 0) return;
  settings.spendingLimit = val;
  saveData();
  renderLimitStatus();
  showToast('Limit pengeluaran disimpan!');
}

function renderLimitStatus() {
  const alertEl = document.getElementById('limitAlert');
  if (!settings.spendingLimit) { alertEl.classList.remove('show'); return; }

  const total = transactions.reduce((s, t) => s + t.amount, 0);
  const el = document.getElementById('limitInput');
  if (el && !el.value) el.value = settings.spendingLimit || '';

  if (total >= settings.spendingLimit) {
    alertEl.textContent = `⚠️ Pengeluaran ${formatRp(total)} melebihi limit ${formatRp(settings.spendingLimit)}!`;
    alertEl.classList.add('show');
  } else {
    alertEl.classList.remove('show');
  }
}

// ---- TABS ----
function switchTab(tab) {
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelector(`.tab-btn[data-tab="${tab}"]`).classList.add('active');
  document.getElementById('panel-' + tab).classList.add('active');
  if (tab === 'chart') renderChart();
  if (tab === 'summary') renderSummary();
}

// ---- TOAST ----
function showToast(msg) {
  const toast = document.getElementById('toast');
  toast.textContent = msg;
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 2200);
}

// ---- HELPERS ----
function escapeHtml(str) {
  return String(str).replace(/[&<>"']/g, s => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[s]));
}

// ---- EVENT LISTENERS ----
function setupEventListeners() {
  document.getElementById('themeToggle').addEventListener('click', () => {
    settings.theme = settings.theme === 'dark' ? 'light' : 'dark';
    saveData();
    applyTheme();
    if (document.getElementById('panel-chart').classList.contains('active')) renderChart();
  });

  document.getElementById('addBtn').addEventListener('click', addTransaction);

  // Enter key on inputs
  ['itemName','itemAmount'].forEach(id => {
    document.getElementById(id).addEventListener('keydown', e => {
      if (e.key === 'Enter') addTransaction();
    });
  });

  document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', () => switchTab(btn.dataset.tab));
  });

  document.getElementById('sortSelect').addEventListener('change', e => {
    currentSort = e.target.value;
    renderTransactionList();
  });

  document.getElementById('btnPrevMonth').addEventListener('click', () => {
    currentMonth--;
    if (currentMonth < 0) { currentMonth = 11; currentYear--; }
    renderSummary();
  });

  document.getElementById('btnNextMonth').addEventListener('click', () => {
    currentMonth++;
    if (currentMonth > 11) { currentMonth = 0; currentYear++; }
    renderSummary();
  });

  document.getElementById('btnSetLimit').addEventListener('click', setSpendingLimit);
  document.getElementById('btnAddCat').addEventListener('click', addCustomCategory);
  document.getElementById('customCatInput').addEventListener('keydown', e => {
    if (e.key === 'Enter') addCustomCategory();
  });
}

// ---- START ----
document.addEventListener('DOMContentLoaded', init);
