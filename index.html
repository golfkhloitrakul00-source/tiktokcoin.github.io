// GetCoinsDemo.jsx
// Single-file React component (default export) — demo app to fetch and display cryptocurrency coins.
// Features:
// - Fetch top 100 coins from CoinGecko
// - Search/filter coins
// - Select a coin to show details and a small price chart (sparkline)
// - Responsive, Tailwind-based layout
// How to run:
// 1. Create a React app (e.g. `npx create-react-app my-app --template cra-template-pwa`)
// 2. Install deps: `npm install react-chartjs-2 chart.js`
// 3. Add Tailwind (optional) or remove Tailwind classes. For quick test, you can keep styles minimal.
// 4. Save this file as `src/GetCoinsDemo.jsx` and import it in `src/App.js`:
//    `import GetCoinsDemo from './GetCoinsDemo';` then use <GetCoinsDemo />.

import React, { useEffect, useState, useMemo } from 'react';
import { Line } from 'react-chartjs-2';
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Tooltip,
  Legend,
} from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Tooltip, Legend);

export default function GetCoinsDemo() {
  const [coins, setCoins] = useState([]);
  const [query, setQuery] = useState('');
  const [selected, setSelected] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  useEffect(() => {
    let canceled = false;
    async function fetchCoins() {
      setLoading(true);
      setError(null);
      try {
        // CoinGecko public markets endpoint
        const res = await fetch(
          'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=true&price_change_percentage=24h'
        );
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        const data = await res.json();
        if (!canceled) setCoins(data);
      } catch (e) {
        if (!canceled) setError(e.message || 'Failed to fetch');
      } finally {
        if (!canceled) setLoading(false);
      }
    }
    fetchCoins();
    return () => (canceled = true);
  }, []);

  const filtered = useMemo(() => {
    const q = query.trim().toLowerCase();
    if (!q) return coins;
    return coins.filter(
      (c) => c.name.toLowerCase().includes(q) || c.symbol.toLowerCase().includes(q) || String(c.market_cap_rank).includes(q)
    );
  }, [coins, query]);

  function selectCoin(coin) {
    setSelected(coin);
    // scroll to details on small screens
    setTimeout(() => document.getElementById('coin-details')?.scrollIntoView({ behavior: 'smooth' }), 200);
  }

  function sparklineData(coin) {
    // coin.sparkline_in_7d.price is usually available when sparkline=true
    const prices = coin?.sparkline_in_7d?.price || [];
    const labels = prices.map((_, i) => i);
    return {
      labels,
      datasets: [
        {
          label: `${coin.name} (7d)`,
          data: prices,
          fill: false,
          tension: 0.25,
          pointRadius: 0,
        },
      ],
    };
  }

  return (
    <div className="min-h-screen p-4 bg-gray-50 text-gray-900">
      <div className="max-w-6xl mx-auto">
        <header className="mb-6">
          <h1 className="text-2xl font-extrabold">GetCoins Demo</h1>
          <p className="text-sm text-gray-600">Simple demo showing live coin market data from CoinGecko.</p>
        </header>

        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <section className="md:col-span-2">
            <div className="mb-4 flex gap-2 items-center">
              <input
                className="flex-1 p-2 border rounded shadow-sm"
                placeholder="Search by name, symbol or rank..."
                value={query}
                onChange={(e) => setQuery(e.target.value)}
              />
              <button
                className="px-3 py-2 bg-blue-600 text-white rounded"
                onClick={() => {
                  setQuery('');
                }}
              >
                Clear
              </button>
            </div>

            <div className="bg-white rounded shadow overflow-auto" style={{ maxHeight: '60vh' }}>
              {loading && <div className="p-4">Loading coins...</div>}
              {error && <div className="p-4 text-red-600">Error: {error}</div>}
              {!loading && !error && (
                <table className="w-full text-sm">
                  <thead className="sticky top-0 bg-gray-100">
                    <tr>
                      <th className="text-left p-2">#</th>
                      <th className="text-left p-2">Coin</th>
                      <th className="text-right p-2">Price (USD)</th>
                      <th className="text-right p-2">24h %</th>
                      <th className="text-right p-2">Market Cap</th>
                    </tr>
                  </thead>
                  <tbody>
                    {filtered.map((c) => (
                      <tr
                        key={c.id}
                        className="cursor-pointer hover:bg-gray-50"
                        onClick={() => selectCoin(c)}
                      >
                        <td className="p-2">{c.market_cap_rank}</td>
                        <td className="p-2 flex items-center gap-2">
                          <img src={c.image} alt="" className="w-6 h-6" />
                          <div>
                            <div className="font-semibold">{c.name}</div>
                            <div className="text-xs text-gray-500">{c.symbol.toUpperCase()}</div>
                          </div>
                        </td>
                        <td className="p-2 text-right">${Number(c.current_price).toLocaleString()}</td>
                        <td
                          className={`p-2 text-right ${c.price_change_percentage_24h >= 0 ? 'text-green-600' : 'text-red-600'}`}
                        >
                          {c.price_change_percentage_24h?.toFixed(2)}%
                        </td>
                        <td className="p-2 text-right">${Number(c.market_cap).toLocaleString()}</td>
                      </tr>
                    ))}
                  </tbody>
                </table>
              )}
            </div>
          </section>

          <aside className="md:col-span-1">
            <div id="coin-details" className="bg-white p-4 rounded shadow">
              {!selected && <div className="text-sm text-gray-600">Select a coin to see details.</div>}
              {selected && (
                <div>
                  <div className="flex items-center gap-3 mb-3">
                    <img src={selected.image} alt="" className="w-10 h-10" />
                    <div>
                      <div className="text-lg font-bold">{selected.name}</div>
                      <div className="text-xs text-gray-500">{selected.symbol.toUpperCase()}</div>
                    </div>
                  </div>

                  <div className="grid grid-cols-2 gap-2 text-sm mb-3">
                    <div>
                      <div className="text-xs text-gray-500">Price</div>
                      <div className="font-medium">${Number(selected.current_price).toLocaleString()}</div>
                    </div>
                    <div>
                      <div className="text-xs text-gray-500">Market Cap</div>
                      <div className="font-medium">${Number(selected.market_cap).toLocaleString()}</div>
                    </div>
                    <div>
                      <div className="text-xs text-gray-500">24h</div>
                      <div className={`font-medium ${selected.price_change_percentage_24h >= 0 ? 'text-green-600' : 'text-red-600'}`}>
                        {selected.price_change_percentage_24h?.toFixed(2)}%
                      </div>
                    </div>
                    <div>
                      <div className="text-xs text-gray-500">Supply</div>
                      <div className="font-medium">{selected.total_supply ? Number(selected.total_supply).toLocaleString() : '—'}</div>
                    </div>
                  </div>

                  <div style={{ height: 160 }}>
                    {selected.sparkline_in_7d?.price?.length ? (
                      <Line data={sparklineData(selected)} options={{
                        plugins: { legend: { display: false } },
                        scales: { x: { display: false }, y: { display: false } },
                        elements: { line: { borderWidth: 1 } },
                        maintainAspectRatio: false,
                      }} />
                    ) : (
                      <div className="text-sm text-gray-500">No sparkline available.</div>
                    )}
                  </div>

                  <div className="mt-3 flex gap-2">
                    <a
                      className="flex-1 text-center p-2 border rounded"
                      href={`https://www.coingecko.com/en/coins/${selected.id}`}
                      target="_blank"
                      rel="noreferrer"
                    >
                      Open on CoinGecko
                    </a>
                    <button
                      className="p-2 bg-gray-100 rounded"
                      onClick={() => {
                        setSelected(null);
                      }}
                    >
                      Close
                    </button>
                  </div>
                </div>
              )}
            </div>

            <div className="mt-4 p-3 text-sm bg-white rounded shadow">
              <div className="font-semibold mb-2">Tips</div>
              <ul className="list-disc pl-5 text-gray-600">
                <li>Public demo — do not use for trading decisions.</li>
                <li>Rate limits: CoinGecko is free but has rate limits for heavy usage.</li>
                <li>You can extend this app with paging, caching, or server-side proxy to avoid CORS/rate limits.</li>
              </ul>
            </div>
          </aside>
        </div>

        <footer className="mt-6 text-xs text-gray-500">Data from CoinGecko (public API)</footer>
      </div>
    </div>
  );
}
