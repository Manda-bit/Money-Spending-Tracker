# 💸 MoneyTrack — Personal Finance Tracker

A fully featured, offline-first personal finance tracker built with React. Log daily expenses, visualize spending patterns, set budgets, and understand where your money goes — all stored locally in your browser with no account or backend required.

---

## ✨ Features

### Transaction Management
- **Quick-add form** always visible with amount, category, description, date, and expense/income toggle
- **Transaction list** grouped by date (Today, Yesterday, or specific date)
- **Search and filter** by keyword, category, and date range
- **Edit any transaction** by clicking on it to open a pre-filled modal
- **Recurring transactions** — mark as Daily, Weekly, or Monthly; auto-added on app load when due

### Dashboard
- **Balance card** showing Total Income, Total Expenses, and Net Balance for the selected period
- **Period selector** — Today, This Week, This Month, This Year
- **Spending by Category** — donut chart with interactive legend
- **Income vs Expenses** — daily bar chart comparison
- **Spending Trend** — cumulative line chart over the current period
- **Top 5 Categories** — horizontal bar list with percentage of total spending

### Budget Manager
- Set a monthly spending limit per category
- Progress bars showing budget used vs. limit — turns orange at 75%, red at 90%
- "Over budget!" badge on categories that exceeded their limit
- Remaining budget displayed per category
- Toast notification when a category reaches 80% of its budget

### Reports
- Monthly summary table with Income, Expenses, Savings, and Savings %
- **Export to CSV** — downloads all transactions as a spreadsheet
- **Export JSON** — full data backup including budgets, categories, and settings

### Settings
- **Currency selector** — USD ($), IDR (Rp), EUR (€), SGD (S$), GBP (£)
- **Category manager** — add custom categories with emoji and name; remove custom ones
- **Data management** — export backup, import from backup, reset all data with confirmation

### Design
- Clean fintech-inspired UI with indigo accent color
- Dark mode toggle, persisted across sessions
- Mobile-responsive with bottom navigation bar on small screens
- Sidebar navigation on desktop

---

## 🗂 File Structure

```
money-tracker/
├── public/
│   └── manifest.json
├── src/
│   ├── pages/
│   │   ├── Dashboard.jsx
│   │   ├── Transactions.jsx
│   │   ├── Budget.jsx
│   │   ├── Reports.jsx
│   │   └── Settings.jsx
│   ├── components/
│   │   ├── TransactionForm.jsx
│   │   ├── TransactionList.jsx
│   │   ├── BudgetProgress.jsx
│   │   └── charts/
│   ├── hooks/
│   │   └── useFinance.js
│   ├── utils/
│   │   ├── formatCurrency.js
│   │   └── dateHelpers.js
│   └── App.jsx
└── README.md
```

---

## 💾 Data Storage

All data is stored in your browser's `localStorage` as JSON under the following keys:

| Key | Description |
|-----|-------------|
| `mt_transactions` | Array of all transaction objects |
| `mt_budgets` | Object mapping category ID to monthly budget amount |
| `mt_categories` | Array of category objects (emoji, name, id) |
| `mt_settings` | User preferences — currency and dark mode |

### Schema

```json
{
  "transactions": [
    {
      "id": "1718000000000",
      "amount": 50.00,
      "type": "expense",
      "category": "food",
      "description": "Groceries",
      "date": "2025-06-23",
      "recurring": "monthly",
      "nextDue": "2025-07-23",
      "createdAt": "2025-06-23T10:00:00.000Z"
    }
  ],
  "budgets": {
    "food": 300,
    "transport": 100
  },
  "categories": [
    { "id": "food", "emoji": "🍔", "name": "Food" }
  ],
  "settings": {
    "currency": "USD",
    "dark": false
  }
}
```

**Default categories:** 🍔 Food, 🚌 Transport, 🏠 Housing, 💊 Health, 🎮 Entertainment, 📚 Education, 🛍️ Shopping, 💰 Income, ➕ Other.

---

## 🔁 Backup & Restore

### Export a backup
1. Go to **Settings** → Data Management → **Export Backup**
2. A file named `moneytrack-backup.json` will be downloaded to your device

### Restore from backup
1. Go to **Settings** → Data Management → **Import Backup**
2. Select your previously exported `.json` file
3. All transactions, budgets, categories, and settings will be restored

> Your data lives entirely in your browser. Clearing browser storage or switching devices will erase it. **Export a backup regularly.**

---

## 📱 PWA — Install on Mobile

MoneyTrack is PWA-ready and can be installed as a home screen app on iOS and Android.

**On Android (Chrome):**
1. Open the app in Chrome
2. Tap the three-dot menu → **Add to Home Screen**
3. Tap **Install**

**On iOS (Safari):**
1. Open the app in Safari
2. Tap the **Share** icon (box with arrow)
3. Tap **Add to Home Screen**
4. Tap **Add**

Once installed, the app runs offline with full functionality.

---

## 🛠 Local Development

### Prerequisites
- Node.js 18 or later
- npm or yarn

### Getting started

```bash
# Clone the repository
git clone https://github.com/your-username/money-tracker.git
cd money-tracker

# Install dependencies
npm install

# Start development server
npm run dev
```

Open `http://localhost:5173` in your browser.

### Build for production

```bash
npm run build
```

The production-ready files will be in the `dist/` folder. Deploy to any static host — Vercel, Netlify, GitHub Pages, or your own server.

### Tech stack

| Tool | Purpose |
|------|---------|
| React 18 | UI framework |
| React Router v6 | Page navigation |
| Recharts | Charts and data visualization |
| date-fns | Date arithmetic and formatting |
| React Hook Form | Form state management |
| jsPDF + html2canvas | PDF export |
| localStorage | Offline data persistence |

---

## 🔐 Privacy

MoneyTrack stores all data locally in your browser. No data is sent to any server. No accounts. No tracking. Everything stays on your device.

---

## 📄 License

MIT License. Free to use, modify, and distribute.
