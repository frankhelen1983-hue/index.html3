<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="VectisAsset - 国际稀土战略终端，提供全球稀土交易数据实时接入与资源清算服务。">
    <title>VectisAsset | 国际稀土战略终端</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&family=JetBrains+Mono:wght@700&display=swap" rel="stylesheet">
    <style>
        :root { --amber: #FFB800; --bg: #05070A; }
        body { background-color: var(--bg); font-family: 'Inter', sans-serif; color: #cbd5e1; margin: 0; }
        .mono { font-family: 'JetBrains Mono', monospace; }
        .glass-panel { 
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.8) 0%, rgba(2, 4, 8, 0.9) 100%);
            backdrop-filter: blur(30px);
            border: 1px solid rgba(255,255,255,0.05);
        }
        .logo-box { 
            background: linear-gradient(135deg, #FFB800 0%, #FF8A00 100%);
            box-shadow: 0 0 30px rgba(255, 184, 0, 0.25);
        }
        .btn-gold { 
            background: linear-gradient(135deg, #FFB800 0%, #D97706 100%);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .btn-gold:hover { transform: translateY(-2px); box-shadow: 0 10px 20px rgba(217, 119, 6, 0.3); }
        input::-webkit-outer-spin-button, input::-webkit-inner-spin-button { -webkit-appearance: none; margin: 0; }
    </style>
</head>
<body class="antialiased">
    <nav class="sticky top-0 z-50 border-b border-white/5 bg-black/60 backdrop-blur-xl h-24">
        <div class="max-w-[1440px] mx-auto px-8 h-full flex items-center justify-between">
            <div class="flex items-center gap-5">
                <div class="w-14 h-14 logo-box rounded-2xl flex items-center justify-center">
                    <svg viewBox="0 0 24 24" class="w-8 h-8 text-black fill-none stroke-current" stroke-width="2.5">
                        <path d="M21 16.09v-8.18a1.64 1.64 0 0 0-.83-1.43L13 2.35a1.63 1.63 0 0 0-1.93 0L3.83 6.48a1.64 1.64 0 0 0-.83 1.43v8.18a1.64 1.64 0 0 0 .83 1.43L11.07 21.65a1.63 1.63 0 0 0 1.93 0l7.24-4.14a1.64 1.64 0 0 0 .83-1.42z"></path>
                        <polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline>
                        <line x1="12" y1="22.08" x2="12" y2="12"></line>
                    </svg>
                </div>
                <div>
                    <h1 class="text-3xl font-black text-white leading-none tracking-tighter uppercase">VECTIS<span class="text-amber-500 italic ml-1">ASSET</span></h1>
                    <p class="text-[9px] font-bold text-slate-500 tracking-[0.45em] uppercase mt-1.5">International REE Terminal</p>
                </div>
            </div>
            <div class="hidden md:flex items-center gap-8 mr-8">
                <a href="#" class="text-[10px] font-black text-slate-400 hover:text-white transition-all tracking-widest uppercase">合规声明</a>
                <button id="connectButton" class="px-8 py-3 bg-white/5 border border-white/10 rounded-2xl text-[10px] font-black uppercase tracking-widest text-white hover:bg-white/10 transition-all">节点连接</button>
            </div>
        </div>
    </nav>

    <main class="max-w-[1440px] mx-auto p-8 lg:p-12">
        <div class="grid grid-cols-1 xl:grid-cols-3 gap-10 mb-12">
            <div class="xl:col-span-2 glass-panel rounded-[48px] p-12 relative overflow-hidden">
                <div class="flex items-center gap-3 mb-10">
                    <span class="w-2.5 h-2.5 rounded-full bg-green-500 animate-pulse"></span>
                    <span class="text-[11px] font-black text-slate-500 uppercase tracking-[0.3em]">全球稀土交易数据实时接入</span>
                </div>
                <p class="text-slate-400 text-sm font-bold uppercase mb-3 italic">稀土氧化物指数: 氧化铽 (Tb4O7)</p>
                <div class="flex flex-col md:flex-row md:items-end gap-6 mb-10">
                    <span id="priceDisplay" class="text-[80px] lg:text-[110px] font-black text-white mono leading-none tracking-tighter italic">$1,425,000</span>
                    <span class="text-amber-500 font-black text-3xl italic tracking-tighter mb-4">USD/MT</span>
                </div>
                <div class="flex gap-10 border-t border-white/5 pt-10">
                    <div>
                        <p class="text-[10px] font-black text-slate-600 uppercase tracking-widest mb-1">今日涨幅</p>
                        <p id="changeDisplay" class="text-green-500 font-bold mono text-xl">+12.45%</p>
                    </div>
                    <div>
                        <p class="text-[10px] font-black text-slate-600 uppercase tracking-widest mb-1">24H 成交量</p>
                        <p class="text-white font-bold mono text-xl">420.5 MT</p>
                    </div>
                </div>
            </div>

            <div class="bg-gradient-to-br from-amber-500 to-amber-600 rounded-[48px] p-12 text-black flex flex-col justify-between shadow-2xl relative overflow-hidden group min-h-[400px]">
                <div class="absolute top-0 right-0 w-48 h-48 bg-white/10 rounded-full blur-3xl -mr-24 -mt-24"></div>
                <div class="relative z-10 flex justify-between items-start">
                    <div>
                        <h3 class="text-[11px] font-black uppercase tracking-widest opacity-60 italic">账户资产净值</h3>
                        <p class="text-xs font-black mono mt-2">ID: 8820-VCT-ASSET</p>
                    </div>
                    <div class="w-12 h-12 bg-black/10 rounded-xl flex items-center justify-center border border-black/5">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
                    </div>
                </div>
                <div class="relative z-10">
                    <p class="text-[12px] font-black uppercase tracking-widest opacity-60 mb-2 italic">Institutional Portfolio</p>
                    <h4 class="text-5xl lg:text-6xl font-black italic mono tracking-tighter leading-none">$24,502,900</h4>
                    <div class="mt-10">
                        <span class="px-6 py-2.5 bg-black text-amber-500 rounded-2xl text-[10px] font-black uppercase tracking-[0.2em] italic">Platinum Verified</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="grid grid-cols-1 xl:grid-cols-12 gap-10">
            <div class="xl:col-span-8 glass-panel rounded-[48px] overflow-hidden">
                <div class="px-10 py-10 border-b border-white/5 flex items-center justify-between">
                    <h3 class="text-xs font-black uppercase tracking-[0.5em] text-white italic">资源清算 Registry</h3>
                    <span id="refreshTime" class="text-[10px] font-bold text-slate-500 uppercase tracking-widest">刷新时间: --:--:--</span>
                </div>
                <div class="overflow-x-auto">
                    <table class="w-full text-left">
                        <tbody class="divide-y divide-white/5">
                            <tr class="hover:bg-white/[0.03] transition-all group">
                                <td class="px-10 py-12 flex items-center gap-6">
                                    <div class="w-14 h-14 bg-slate-900 border border-white/10 rounded-2xl flex items-center justify-center font-black text-amber-500 italic text-lg shadow-inner group-hover:border-amber-500/50 transition-colors">Nd</div>
                                    <div>
                                        <p class="text-lg font-black text-white uppercase tracking-tight leading-none">氧化钕 (Nd2O3)</p>
                                        <p class="text-[10px] font-bold text-slate-600 uppercase tracking-widest mt-2 italic">Purity 99.9% | Global Stockpile</p>
                                    </div>
                                </td>
                                <td class="px-10 py-12 text-2xl font-black mono text-white italic tracking-tighter">$112,400.00</td>
                                <td class="px-10 py-12 text-right">
                                    <button class="px-10 py-4 bg-white/5 border border-white/10 rounded-2xl text-[11px] font-black uppercase tracking-widest text-white hover:bg-amber-500 hover:text-black transition-all">确认结算</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <div class="xl:col-span-4 glass-panel rounded-[48px] p-12 flex flex-col justify-center">
                <h3 class="text-[11px] font-black uppercase tracking-[0.4em] text-white mb-10 italic text-center">指令下达终端</h3>
                <div class="space-y-8">
                    <div class="space-y-4">
                        <label class="text-[11px] font-black text-slate-500 uppercase tracking-widest ml-1 italic">购买数量 (MT)</label>
                        <input type="number" placeholder="0.00 MT" class="w-full bg-black/50 border border-white/10 rounded-[32px] p-8 text-4xl font-black mono text-white outline-none focus:border-amber-500 text-center italic shadow-inner transition-all">
                    </div>
                    <button id="tradeButton" class="w-full py-8 btn-gold rounded-[32px] text-black font-black text-sm uppercase tracking-[0.5em] italic shadow-2xl active:scale-95">
                        授权交易协议
                    </button>
                    <p class="text-[9px] text-center text-slate-700 font-black uppercase tracking-[0.4em]">Infrastructure Validated by REE Protocol</p>
                </div>
            </div>
        </div>
    </main>

    <footer class="mt-40 pb-24 text-center border-t border-white/5 pt-16 bg-black/20">
        <div class="flex flex-col items-center gap-6 opacity-30">
            <div class="flex items-center gap-3">
                <div class="w-8 h-8 bg-slate-800 rounded-lg flex items-center justify-center font-black text-amber-500 italic text-xs">V</div>
                <span class="text-[10px] font-black tracking-[0.5em] text-slate-400 uppercase italic">VectisAsset Digital Infrastructure</span>
            </div>
            <p class="text-[10px] text-slate-800 font-black uppercase tracking-[0.8em]">Global Strategic Terminal © 2026</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // 实时更新刷新时间
            function updateTime() {
                const now = new Date();
                const timeStr = now.getHours().toString().padStart(2, '0') + ":" + 
                                now.getMinutes().toString().padStart(2, '0') + ":" + 
                                now.getSeconds().toString().padStart(2, '0');
                document.getElementById('refreshTime').textContent = "刷新时间: " + timeStr;
            }
            setInterval(updateTime, 1000);
            updateTime();

            // 价格模拟器优化
            function simulatePriceChange() {
                const priceElement = document.getElementById('priceDisplay');
                const changeElement = document.getElementById('changeDisplay');
                if (!priceElement || !changeElement) return;

                let currentPrice = parseFloat(priceElement.textContent.replace(/[^0-9.-]+/g, ""));
                const changePercent = (Math.random() - 0.5) * 1.5; 
                const newPrice = currentPrice * (1 + changePercent / 100);

                priceElement.textContent = '$' + Math.round(newPrice).toLocaleString();
                changeElement.textContent = (changePercent > 0 ? '+' : '') + changePercent.toFixed(2) + '%';
                changeElement.className = "font-bold mono text-xl " + (changePercent >= 0 ? 'text-green-500' : 'text-red-500');
            }
            setInterval(simulatePriceChange, 4000);

            // 交互逻辑
            document.getElementById('connectButton').addEventListener('click', function() {
                this.textContent = '已连接至终端';
                this.className = "px-8 py-3 bg-green-500/10 border border-green-500/50 rounded-2xl text-[10px] font-black uppercase tracking-widest text-green-500 transition-all";
            });

            document.getElementById('tradeButton').addEventListener('click', function() {
                const btn = this;
                btn.textContent = '协议执行中...';
                btn.style.opacity = '0.7';
                setTimeout(() => {
                    alert('【系统通知】交易授权协议已通过区块链节点验证并提交。');
                    btn.textContent = '授权交易协议';
                    btn.style.opacity = '1';
                }, 2000);
            });
        });
    </script>
</body>
</html>
