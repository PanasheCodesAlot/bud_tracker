<script lang="ts">
	import { fade, fly } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';
	import { 
		Leaf, 
		Wallet, 
		TrendingUp, 
		Sparkles, 
		Download, 
		Flame, 
		Layers,
		CheckCircle2,
		ShieldCheck,
		FileText,
		DownloadCloud,
		User,
		Medal,
		Compass,
		Smile,
		ChevronRight,
		Info,
		RotateCcw
	} from 'lucide-svelte';

	// --- Svelte 5 Runes for Interactive State Management ---
	let weeklyGrams = $state(4);
	let pricePerGram = $state(4000); 
	let activePreviewTab = $state('dashboard');
	let currentGuideStep = $state(0);

	// Derived state calculations using runes
	let monthlySpend = $derived(weeklyGrams * 4 * pricePerGram);
	let yearlySpend = $derived(monthlySpend * 12);

	// App Features Array mapping out your newly uploaded screenshots
	const appFeatures = [
		{
			id: 'dashboard',
			title: 'Gamified Ranking Matrix',
			badge: 'Couch Potato Rank',
			description: 'Start from a stationary lounge chair icon and tier up your rank as your tracking metrics mature securely over time.',
			icon: User,
			color: 'text-emerald-400',
			bg: 'bg-emerald-500/10'
		},
		{
			id: 'milestones',
			title: 'Sovereign Shields & Milestones',
			badge: 'Goal Achieved',
			description: 'Earn gamified tokens like the Sovereign Shield for configuring strict monthly budget safety limits or maintaining active T-breaks.',
			icon: ShieldCheck,
			color: 'text-purple-400',
			bg: 'bg-purple-500/10'
		},
		{
			id: 'export',
			title: 'Clean Data Archival Exports',
			badge: 'TXT & PDF Support',
			description: 'Generate full encrypted local structural reports details of your native strains, absolute buys, and timelines instantly.',
			icon: FileText,
			color: 'text-cyan-400',
			bg: 'bg-cyan-500/10'
		},
		{
			id: 'guide',
			title: 'Mindful Breathing Guide',
			badge: 'Wellness Companion',
			description: 'Regulate inhalations, holds, and exhalations with elegant visual cadence cues designed to protect consumption paces.',
			icon: Compass,
			color: 'text-amber-400',
			bg: 'bg-amber-500/10'
		}
	];

	// Guide Walkthrough Content Mock
	const guideSteps = [
		{ title: 'Track Sessions & Strains', desc: 'Map out your custom herbal strain library. Log smoking, aromatherapy, or vaping logs, trace strain types, and monitor wellness profiles safely.' },
		{ title: 'Keep Spending in Check', desc: 'Record transactions, input grams, and view real-time expense charts. Stay strictly protected within your monthly cash safety budget limit.' },
		{ title: 'Meditation & Breathing Tool', desc: 'Keep centered with the built-in breathing guide. Regulate your inhalations, holds, and exhalations with elegant visual guidance.' }
	];
</script>

<div class="min-h-screen bg-[#070A13] text-slate-100 font-sans selection:bg-emerald-500 selection:text-black overflow-x-hidden">
	
	<div class="absolute top-0 left-1/3 w-[500px] h-[500px] bg-emerald-500/5 rounded-full blur-[140px] pointer-events-none" />
	<div class="absolute top-[120vh] right-1/4 w-[400px] h-[400px] bg-purple-500/5 rounded-full blur-[140px] pointer-events-none" />

	<header class="border-b border-slate-900 bg-[#070A13]/80 backdrop-blur-md sticky top-0 z-50">
		<div class="container mx-auto px-6 py-4 flex justify-between items-center">
			<div class="flex items-center gap-2.5">
				<div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-emerald-500 to-teal-400 flex items-center justify-center shadow-md shadow-emerald-500/10">
					<Leaf class="w-4 h-4 text-[#070A13] stroke-[2.5]" />
				</div>
				<span class="text-lg font-bold tracking-tight text-white flex items-center gap-1.5">
					BudTracker <span class="text-[10px] bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 px-2 py-0.5 rounded-md font-mono">v2.0</span>
				</span>
			</div>
			<div class="flex items-center gap-4">
				<a href="#features" class="text-xs text-slate-400 hover:text-slate-200 transition">Features</a>
				<a href="#calculator" class="text-xs text-slate-400 hover:text-slate-200 transition">Calculator</a>
				<a 
					href="#download" 
					class="px-4 py-2 rounded-xl bg-slate-900 border border-slate-800 hover:border-emerald-500/40 transition-all text-xs font-medium text-slate-200 flex items-center gap-2"
				>
					<DownloadCloud class="w-3.5 h-3.5" /> Install App
				</a>
			</div>
		</div>
	</header>

	<section class="container mx-auto px-6 pt-16 pb-24 grid lg:grid-cols-12 gap-12 items-center relative z-10">
		<div class="lg:col-span-7 space-y-6 text-center lg:text-left" in:fly={{ y: 20, duration: 600 }}>
			<div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 text-xs font-medium">
				<span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse" /> Fresh May 2026 Architectural Release
			</div>
			
			<h1 class="text-4xl md:text-6xl font-black tracking-tight leading-[1.1] text-white">
				Your Mindful Herbal Companion.<br />
				<span class="bg-clip-text text-transparent bg-gradient-to-r from-emerald-400 via-teal-300 to-purple-400">
					Gamified & Guarded.
				</span>
			</h1>
			
			<p class="text-base text-slate-400 max-w-xl mx-auto lg:mx-0 leading-relaxed font-normal">
				Take programmatic control over your wellness goals, budget limits, and native strains. Monitor session frequencies while rising up ranks with secure, completely local storage.
			</p>

			<div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start pt-2">
				<a 
					href="#download" 
					class="px-6 py-3.5 rounded-xl bg-gradient-to-r from-emerald-500 to-teal-500 text-slate-950 font-bold shadow-lg shadow-emerald-500/10 hover:scale-[1.01] transition-all flex items-center justify-center gap-2 text-sm"
				>
					Get BudTracker Now <ChevronRight class="w-4 h-4" />
				</a>
				<a 
					href="#features" 
					class="px-6 py-3.5 rounded-xl bg-slate-900/60 border border-slate-800 hover:border-slate-700 font-medium text-slate-300 transition-all text-sm flex items-center justify-center gap-2"
				>
					Explore Features Demo
				</a>
			</div>
		</div>

		<div class="lg:col-span-5 flex justify-center relative">
			<div class="absolute inset-0 bg-emerald-500/10 rounded-[48px] blur-3xl pointer-events-none transform scale-75" />

			<div class="w-[330px] bg-[#090D1A] border-4 border-slate-900 rounded-[44px] shadow-2xl relative overflow-hidden flex flex-col h-[640px]">
				
				<div class="flex justify-between items-center text-[11px] text-slate-500 font-medium px-6 pt-3 pb-2 bg-[#090D1A]">
					<span>05:44</span>
					<div class="flex items-center gap-1">
						<span>4G LTE</span>
						<div class="w-5 h-2.5 border border-slate-600 rounded-sm p-0.5 flex items-center"><div class="w-full h-full bg-emerald-400 rounded-2xs"></div></div>
					</div>
				</div>

				<div class="px-4 py-3 bg-[#0E1324] border-b border-slate-900/60 flex justify-between items-center">
					<div>
						<div class="flex items-center gap-1.5">
							<Leaf class="w-4 h-4 text-emerald-400" />
							<span class="text-xs font-bold tracking-tight text-white">Bud Tracker</span>
						</div>
						<p class="text-[9px] text-slate-500 font-mono mt-0.5">Hey Allen • May 2026</p>
					</div>
					<div class="flex items-center gap-1.5">
						<span class="text-[9px] bg-slate-900 px-2 py-0.5 border border-slate-800 rounded text-slate-400 flex items-center gap-1">🛋️ Couch Potato</span>
						<div class="w-6 h-6 rounded-full bg-slate-800 border border-slate-700 flex items-center justify-center text-[10px] text-slate-300">👤</div>
					</div>
				</div>

				<div class="flex-1 overflow-y-auto p-4 space-y-4 custom-scrollbar bg-[#070A14]">
					{#if activePreviewTab === 'dashboard'}
						<div class="p-4 bg-[#0E1324] border border-slate-800 rounded-2xl space-y-3">
							<div class="flex justify-between items-center">
								<span class="text-[10px] uppercase font-semibold tracking-wider text-slate-400">Remaining Budget</span>
								<span class="text-[10px] text-rose-400 font-semibold">Monthly Spent: K 0</span>
							</div>
							<div class="flex items-baseline gap-1">
								<span class="text-2xl font-black text-white font-mono">K 25,000</span>
							</div>
							<div class="w-full h-1.5 bg-slate-950 rounded-full overflow-hidden">
								<div class="w-full h-full bg-emerald-500 rounded-full" />
							</div>
							<div class="flex justify-between text-[9px] text-slate-500 font-mono">
								<span>Tap block to adjust limit</span>
								<span>Limit: K 25,000</span>
							</div>
						</div>

						<div class="grid grid-cols-2 gap-2.5">
							<div class="p-3 bg-[#0E1324] border border-slate-800/80 rounded-xl flex items-center gap-2.5">
								<div class="w-7 h-7 rounded-lg bg-emerald-500/10 flex items-center justify-center text-emerald-400 text-xs">🛍️</div>
								<div>
									<p class="text-[9px] text-slate-500">Bought Total</p>
									<p class="text-xs font-bold text-slate-200">0.0g</p>
								</div>
							</div>
							<div class="p-3 bg-[#0E1324] border border-slate-800/80 rounded-xl flex items-center gap-2.5">
								<div class="w-7 h-7 rounded-lg bg-purple-500/10 flex items-center justify-center text-purple-400 text-xs">🔥</div>
								<div>
									<p class="text-[9px] text-slate-500">Sessions</p>
									<p class="text-xs font-bold text-slate-200">0 Total</p>
								</div>
							</div>
						</div>

						<div class="space-y-1.5">
							<p class="text-[10px] font-bold text-slate-400">Recent Activity</p>
							<div class="p-6 bg-[#0E1324]/40 border border-dashed border-slate-800 rounded-xl text-center flex flex-col items-center justify-center">
								<span class="text-xl opacity-30 mb-1">🛒</span>
								<p class="text-[10px] text-slate-500">No history logged yet. Tap button below to begin.</p>
							</div>
						</div>

					{:else if activePreviewTab === 'milestones'}
						<div class="p-4 bg-[#11172B] border border-emerald-500/30 rounded-2xl text-center space-y-3 relative overflow-hidden" in:fade>
							<div class="absolute top-0 inset-x-0 h-1 bg-gradient-to-r from-emerald-500 to-teal-400" />
							<div class="flex justify-center items-center gap-1.5 text-xs font-bold text-emerald-400">
								🛡️ Goal Achieved! 🎉
							</div>
							
							<div class="w-12 h-12 rounded-full bg-emerald-500/10 mx-auto border border-emerald-500/20 flex items-center justify-center text-xl shadow-lg">
								🛡️
							</div>

							<div>
								<h5 class="text-xs font-bold text-white tracking-wide">Sovereign Shield Unlocked</h5>
								<p class="text-[10px] text-slate-400 mt-1 leading-normal">
									Fortified walls! You configured a monthly safety budget limit in your personal local database settings.
								</p>
							</div>

							<button class="w-full py-1.5 bg-emerald-500 text-slate-950 font-bold rounded-lg text-[10px] tracking-wide hover:opacity-90">
								Stay Elevated! 🌿
							</button>
						</div>

						<div class="p-3 bg-[#0E1324] border border-slate-800 rounded-xl space-y-2">
							<div class="flex justify-between items-center border-b border-slate-900 pb-1.5 text-[10px]">
								<span class="text-slate-400 font-semibold">Active Wellness Trackers</span>
								<span class="text-emerald-400">View All 🔍</span>
							</div>
							<div class="flex justify-between items-center text-[10px] p-1.5 bg-slate-950/40 rounded">
								<span class="text-slate-300">⏳ T-Break Champion (48h)</span>
								<span class="text-[9px] bg-slate-900 px-1.5 py-0.5 border border-slate-800 rounded text-slate-500">Locked 🔒</span>
							</div>
							<div class="flex justify-between items-center text-[10px] p-1.5 bg-slate-950/40 rounded">
								<span class="text-slate-300">⚖️ Budget Vigilant Cap</span>
								<span class="text-[9px] text-emerald-400 font-medium">Within Limit 🟢</span>
							</div>
						</div>

					{:else if activePreviewTab === 'export'}
						<div class="p-4 bg-[#0E1324] border border-slate-800 rounded-2xl space-y-3.5" in:fade>
							<div class="flex items-center gap-2">
								<div class="w-6 h-6 bg-cyan-500/10 text-cyan-400 rounded-md flex items-center justify-center text-xs">💾</div>
								<h5 class="text-xs font-bold text-white">Export Bud Tracker Data</h5>
							</div>
							<p class="text-[10px] text-slate-400 leading-relaxed">
								Generates a structural offline backup report detail breakdown of your native flower strains, buys, and timeline logs.
							</p>

							<div class="grid grid-cols-2 gap-2 pt-1">
								<div class="p-2 border border-slate-800 hover:border-slate-700 bg-slate-950/50 rounded-xl text-center text-[10px] font-medium text-emerald-400 cursor-pointer transition">
									Export TXT
								</div>
								<div class="p-2 border border-slate-800 hover:border-slate-700 bg-slate-950/50 rounded-xl text-center text-[10px] font-medium text-emerald-400 cursor-pointer transition">
									Export PDF
								</div>
							</div>
						</div>

						<div class="p-3 bg-[#0E1324] border border-slate-800 rounded-xl space-y-2">
							<p class="text-[10px] font-bold text-slate-400">Local Strains Configured</p>
							<div class="text-[9px] font-mono space-y-1 text-slate-500">
								<div class="flex justify-between text-slate-300"><span>🌿 Popcorn</span> <span class="text-emerald-400">K 4,000/g</span></div>
								<div class="flex justify-between text-slate-300"><span>🌿 Sour Peach</span> <span class="text-emerald-400">K 4,000/g</span></div>
								<div class="flex justify-between text-slate-300"><span>🌿 Blue Diesel</span> <span class="text-emerald-400">K 4,000/g</span></div>
							</div>
						</div>

					{:else if activePreviewTab === 'guide'}
						<div class="p-4 bg-[#0E1324] border border-slate-800 rounded-2xl space-y-3 text-center" in:fade>
							<div class="flex justify-between text-[9px] font-mono text-slate-500">
								<span class="text-emerald-400">Step {currentGuideStep + 1} of 3: Quick Guide</span>
								<span class="cursor-pointer hover:text-white">Skip</span>
							</div>

							<div class="w-10 h-10 rounded-full bg-emerald-500/10 mx-auto flex items-center justify-center text-emerald-400">
								{#if currentGuideStep === 0}🍃{:else if currentGuideStep === 1}🛍️{:else}🧘{/if}
							</div>

							<div class="space-y-1">
								<h6 class="text-xs font-bold text-slate-200">{guideSteps[currentGuideStep].title}</h6>
								<p class="text-[9px] text-slate-400 leading-normal">{guideSteps[currentGuideStep].desc}</p>
							</div>

							<div class="flex justify-center gap-1.5 py-1">
								{#each guideSteps as _, idx}
									<div class="w-1.5 h-1.5 rounded-full transition-all {idx === currentGuideStep ? 'bg-emerald-400 w-3' : 'bg-slate-800'}" />
								{/each}
							</div>

							<div class="grid grid-cols-2 gap-2 pt-1 text-[10px] font-medium">
								<button 
									disabled={currentGuideStep === 0}
									onclick={() => currentGuideStep = Math.max(0, currentGuideStep - 1)}
									class="py-1 border border-slate-800 hover:border-slate-700 rounded-md text-slate-400 disabled:opacity-30"
								>
									Back
								</button>
								<button 
									onclick={() => currentGuideStep = (currentGuideStep + 1) % 3}
									class="py-1 bg-emerald-500 text-slate-950 font-bold rounded-md"
								>
									{currentGuideStep === 2 ? 'Reset 🔄' : 'Next'}
								</button>
							</div>
						</div>
					{/if}
				</div>

				<div class="p-2.5 bg-[#0E1324] border-t border-slate-900/80 grid grid-cols-5 gap-1 text-center items-center">
					<button onclick={() => activePreviewTab = 'dashboard'} class="flex flex-col items-center gap-0.5 text-slate-500 transition {activePreviewTab === 'dashboard' ? 'text-emerald-400 font-bold' : ''}">
						<span class="text-sm">🎛️</span>
						<span class="text-[8px] tracking-tight">Home</span>
					</button>
					<button onclick={() => activePreviewTab = 'milestones'} class="flex flex-col items-center gap-0.5 text-slate-500 transition {activePreviewTab === 'milestones' ? 'text-purple-400 font-bold' : ''}">
						<span class="text-sm">✨</span>
						<span class="text-[8px] tracking-tight">Vibes</span>
					</button>
					
					<div class="flex justify-center -translate-y-2">
						<div class="w-8 h-8 rounded-full bg-emerald-500 text-slate-950 font-bold flex items-center justify-center text-sm shadow-md shadow-emerald-500/20 ring-4 ring-[#0E1324]">
							＋
						</div>
					</div>

					<button onclick={() => activePreviewTab = 'export'} class="flex flex-col items-center gap-0.5 text-slate-500 transition {activePreviewTab === 'export' ? 'text-cyan-400 font-bold' : ''}">
						<span class="text-sm">🌿</span>
						<span class="text-[8px] tracking-tight">Strains</span>
					</button>
					<button onclick={() => activePreviewTab = 'guide'} class="flex flex-col items-center gap-0.5 text-slate-500 transition {activePreviewTab === 'guide' ? 'text-amber-400 font-bold' : ''}">
						<span class="text-sm">🧘</span>
						<span class="text-[8px] tracking-tight">Habit</span>
					</button>
				</div>

				<div class="py-1.5 bg-[#0E1324] flex justify-center items-center">
					<div class="w-24 h-1 bg-slate-700 rounded-full" />
				</div>
			</div>
		</div>
	</section>

	<hr class="border-slate-900 container mx-auto" />

	<section id="features" class="container mx-auto px-6 py-20 relative z-10">
		<div class="text-center max-w-2xl mx-auto mb-16 space-y-3">
			<h2 class="text-2xl md:text-3xl font-extrabold text-white tracking-tight">
				Engineered for Mindful Tracking Rituals
			</h2>
			<p class="text-slate-400 text-sm">
				Click tabs on either side to control the live reactive mobile screen framework and inspect the system elements interactively.
			</p>
		</div>

		<div class="grid md:grid-cols-2 lg:grid-cols-4 gap-4">
			{#each appFeatures as feature}
				<button 
					onclick={() => activePreviewTab = feature.id}
					class="p-5 rounded-2xl border text-left transition-all relative overflow-hidden group {activePreviewTab === feature.id ? 'bg-[#0E1324] border-slate-700 shadow-xl ring-1 ring-slate-800' : 'bg-transparent border-slate-900 hover:bg-[#0E1324]/40 hover:border-slate-800'}"
				>
					<div class="flex items-center justify-between mb-4">
						<div class="p-2.5 rounded-xl transition-all {feature.bg} {feature.color}">
							<svelte:component this={feature.icon} class="w-5 h-5" />
						</div>
						<span class="text-[9px] font-mono font-medium px-2 py-0.5 bg-slate-900 border border-slate-800/80 rounded text-slate-400 group-hover:text-emerald-400 transition-colors">
							{feature.badge}
						</span>
					</div>
					<h3 class="font-bold text-sm text-white mb-1.5 tracking-tight group-hover:text-emerald-400 transition-colors">
						{feature.title}
					</h3>
					<p class="text-xs text-slate-400 leading-relaxed font-normal">
						{feature.description}
					</p>
				</button>
			{/each}
		</div>
	</section>

	<section id="calculator" class="py-16 bg-[#090D1A]/60 border-t border-b border-slate-900 relative">
		<div class="container mx-auto px-6 max-w-4xl">
			<div class="text-center mb-10 space-y-2">
				<div class="inline-flex items-center gap-1 px-2 py-0.5 rounded bg-purple-500/10 border border-purple-500/20 text-purple-400 text-[10px] font-mono uppercase tracking-wider">
					<TrendingUp class="w-3 h-3" /> Budget Optimization Engine
				</div>
				<h2 class="text-2xl font-bold text-white tracking-tight">Interactive Stash Projection Calculator</h2>
				<p class="text-xs text-slate-400">Map your metrics to see exactly how your monthly allocation limits operate under local pricing metrics.</p>
			</div>

			<div class="grid md:grid-cols-12 gap-6 bg-[#0E1324] border border-slate-800/80 rounded-2xl p-6 shadow-xl items-center">
				<div class="md:col-span-7 space-y-5">
					<div class="space-y-2">
						<div class="flex justify-between text-xs font-medium">
							<span class="text-slate-400">Weekly Target Footprint</span>
							<span class="text-emerald-400 font-bold font-mono">{weeklyGrams} Grams</span>
						</div>
						<input 
							type="range" min="1" max="20" 
							bind:value={weeklyGrams} 
							class="w-full h-1.5 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-emerald-500"
						/>
					</div>

					<div class="space-y-2">
						<div class="flex justify-between text-xs font-medium">
							<span class="text-slate-400">Market Price Standard per Gram</span>
							<span class="text-emerald-400 font-bold font-mono">K {pricePerGram.toLocaleString()}</span>
						</div>
						<input 
							type="range" min="2000" max="10000" step="500"
							bind:value={pricePerGram} 
							class="w-full h-1.5 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-emerald-500"
						/>
					</div>
				</div>

				<div class="md:col-span-5 p-5 rounded-xl bg-slate-950/60 border border-slate-900 space-y-3.5">
					<div>
						<p class="text-[10px] text-slate-500 uppercase tracking-wider font-semibold">Monthly Limit Equivalent</p>
						<p class="text-2xl font-black text-white font-mono mt-0.5">K {monthlySpend.toLocaleString()}</p>
					</div>
					<div class="h-px bg-slate-900" />
					<div>
						<p class="text-[10px] text-slate-500 uppercase tracking-wider font-semibold">Yearly Investment Matrix</p>
						<p class="text-base font-bold text-purple-400 font-mono mt-0.5">K {yearlySpend.toLocaleString()}</p>
					</div>
					<div class="flex items-start gap-1.5 p-2 bg-emerald-500/5 rounded border border-emerald-500/10 text-[10px] text-slate-400 leading-normal">
						<Info class="w-3.5 h-3.5 text-emerald-400 shrink-0 mt-0.5" />
						<span>Setting a rigid safety block saves users an average of 15% across native cycles!</span>
					</div>
				</div>
			</div>
		</div>
	</section>

	<section id="download" class="container mx-auto px-6 py-20 text-center relative max-w-3xl">
		<div class="bg-gradient-to-b from-[#0E1324] to-[#090D1A] border border-slate-800/80 rounded-3xl p-10 space-y-6 shadow-2xl relative z-10">
			<div class="w-12 h-12 rounded-2xl bg-gradient-to-tr from-emerald-500 to-teal-400 flex items-center justify-center shadow-lg shadow-emerald-500/10 mx-auto">
				<Leaf class="w-5 h-5 text-slate-950 stroke-[2.5]" />
			</div>
			
			<div class="space-y-2 max-w-lg mx-auto">
				<h2 class="text-2xl md:text-3xl font-extrabold text-white tracking-tight">Stay Protected. Stay Elevated.</h2>
				<p class="text-slate-400 text-xs md:text-sm leading-relaxed">
					Download the secure local application package today. No cloud accounts, zero trackable marketing telemetry data, 100% offline security.
				</p>
			</div>

			<div class="flex flex-wrap gap-3 justify-center items-center pt-2">
				<button class="px-5 py-3 rounded-xl bg-white text-slate-950 font-bold hover:bg-slate-100 transition text-xs shadow-md shadow-white/5">
					<a href="/Bud Tracker (1).apk" download="">Download Android APK</a>
				</button>
				<button class="px-5 py-3 rounded-xl bg-slate-900 border border-slate-800 hover:border-slate-700 font-semibold text-slate-200 transition text-xs">
					<a href="/Bud Tracker (1).apk" download="">Launch Web PWA Sandbox</a>
				</button>
			</div>

			<div class="pt-4 flex justify-center gap-5 text-[11px] text-slate-500 font-medium">
				<span class="flex items-center gap-1"><CheckCircle2 class="w-3.5 h-3.5 text-emerald-400" /> Offline Backups</span>
				<span class="flex items-center gap-1"><CheckCircle2 class="w-3.5 h-3.5 text-emerald-400" /> Zero Telemetry Tracking</span>
			</div>
		</div>
	</section>

	<footer class="py-6 border-t border-slate-900 bg-slate-950/40 text-center text-[11px] text-slate-500">
		<p>© 2026 BudTracker application architecture. Designed for mindful green consumption goals.</p>
	</footer>
</div>

<style>
	/* Subtle style modifiers for ranges inside sliders */
	input[type='range']::-webkit-slider-thumb {
		box-shadow: 0px 0px 8px rgba(16, 185, 129, 0.4);
		transition: transform 0.1s ease;
	}
	input[type='range']::-webkit-slider-thumb:active {
		transform: scale(1.2);
	}
	.custom-scrollbar::-webkit-scrollbar {
		width: 3px;
	}
	.custom-scrollbar::-webkit-scrollbar-thumb {
		background: #1e293b;
		border-radius: 9px;
	}
</style>