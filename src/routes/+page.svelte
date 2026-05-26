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
		CheckCircle2
	} from 'lucide-svelte';

	// --- Svelte 5 Runes for State Management ---
	let weeklyGrams = $state(3);
	let pricePerGram = $state(4000); // Baseline MK value from your screenshots
	let activeTab = $state('track');

	// Derived state handles calculations cleanly automatically
	let monthlySpend = $derived(weeklyGrams * 4 * pricePerGram);
	let yearlySpend = $derived(monthlySpend * 12);

	const features = [
		{
			id: 'track',
			title: 'Session Logging',
			description: 'Log your favorite local flowers (Popcorn, Blue Diesel) and sessions with a single tap. Keep tabs on your vibes and consumption patterns effortlessly.',
			icon: Flame,
			color: 'text-purple-400',
			bg: 'bg-purple-500/10'
		},
		{
			id: 'budget',
			title: 'Smart Budgeting',
			description: 'Set your monthly limit in Malawi Kwacha (MK). Visually monitor your remaining budget in real-time before you overspend.',
			icon: Wallet,
			color: 'text-emerald-400',
			bg: 'bg-emerald-500/10'
		},
		{
			id: 'insights',
			title: 'AI Budtender',
			description: 'Get deep, personalized insights into your stash, spend habits, and tolerance breaks based on your actual data trends.',
			icon: Sparkles,
			color: 'text-cyan-400',
			bg: 'bg-cyan-500/10'
		}
	];
</script>

<div class="min-h-screen bg-[#0B0F19] text-slate-100 font-sans selection:bg-emerald-500 selection:text-black overflow-x-hidden">
	
	<div class="absolute top-0 left-1/4 w-96 h-96 bg-emerald-500/10 rounded-full blur-[120px] pointer-events-none" />
	<div class="absolute top-1/3 right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-[120px] pointer-events-none" />

	<header class="container mx-auto px-6 py-6 flex justify-between items-center relative z-10">
		<div class="flex items-center gap-2">
			<div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-emerald-500 to-teal-400 flex items-center justify-center shadow-lg shadow-emerald-500/20">
				<Leaf class="w-5 h-5 text-[#0B0F19] stroke-[2.5]" />
			</div>
			<span class="text-xl font-bold tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-white to-slate-400">
				BudTracker
			</span>
		</div>
		<a 
			href="#download" 
			class="px-5 py-2.5 rounded-xl bg-slate-900 border border-slate-800 hover:border-emerald-500/50 transition-all duration-300 flex items-center gap-2 text-sm font-medium text-slate-300 hover:text-white"
		>
			<Download class="w-4 h-4" /> Download App
		</a>
	</header>

	<section class="container mx-auto px-6 pt-12 pb-24 relative z-10 grid lg:grid-cols-12 gap-12 items-center">
		<div class="lg:col-span-7 space-y-8 text-center lg:text-left" in:fly={{ y: 30, duration: 800, easing: cubicOut }}>
			<div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 text-xs font-medium tracking-wide uppercase">
				<Sparkles class="w-3.5 h-3.5" /> Elevate Your Consumption Habits
			</div>
			
			<h1 class="text-5xl md:text-6xl font-extrabold tracking-tight leading-[1.1] text-white">
				Track your sessions.<br />
				<span class="bg-clip-text text-transparent bg-gradient-to-r from-emerald-400 via-teal-300 to-purple-400">
					Master your budget.
				</span>
			</h1>
			
			<p class="text-lg text-slate-400 max-w-2xl mx-auto lg:mx-0 font-normal leading-relaxed">
				The ultimate companion app for modern stoners. Log your favorite local strains, track your daily streaks, control your financial investment, and enjoy a mindful relationship with your bud.
			</p>

			<div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start pt-4">
				<a 
					href="#download" 
					class="px-8 py-4 rounded-2xl bg-gradient-to-r from-emerald-500 to-teal-500 text-[#0B0F19] font-semibold shadow-xl shadow-emerald-500/20 hover:shadow-emerald-500/30 hover:scale-[1.02] transition-all duration-300 flex items-center justify-center gap-3 group"
				>
					Get BudTracker Free
					<Download class="w-5 h-5 transition-transform group-hover:translate-y-0.5" />
				</a>
				<a 
					href="#calculator" 
					class="px-8 py-4 rounded-2xl bg-slate-900/80 border border-slate-800 hover:bg-slate-900 hover:border-slate-700 font-medium text-slate-300 transition-all duration-300 flex items-center justify-center gap-2"
				>
					Calculate Your Stash Spend
				</a>
			</div>

			<div class="grid grid-cols-3 gap-4 pt-8 border-t border-slate-900 max-w-md mx-auto lg:mx-0">
				<div>
					<p class="text-2xl font-bold text-white">100%</p>
					<p class="text-xs text-slate-500 uppercase tracking-wider mt-1">Private & Secure</p>
				</div>
				<div>
					<p class="text-2xl font-bold text-white">0 MK</p>
					<p class="text-xs text-slate-500 uppercase tracking-wider mt-1">Always Free Ads</p>
				</div>
				<div>
					<p class="text-2xl font-bold text-white">4.9★</p>
					<p class="text-xs text-slate-500 uppercase tracking-wider mt-1">User Rating</p>
				</div>
			</div>
		</div>

		<div class="lg:col-span-5 relative flex justify-center" in:fly={{ x: 50, duration: 1000, delay: 200, easing: cubicOut }}>
			<div class="absolute inset-0 bg-gradient-to-tr from-purple-500/20 to-emerald-500/20 rounded-[40px] blur-2xl transform rotate-6 scale-95 pointer-events-none" />

			<div class="w-[320px] bg-[#0E1322] border border-slate-800 rounded-[40px] p-5 shadow-2xl relative overflow-hidden ring-4 ring-slate-900">
				<div class="flex justify-between items-center text-slate-500 text-xs px-2 pb-4 border-b border-slate-900">
					<span>05:43</span>
					<div class="flex items-center gap-1.5">
						<span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse" />
						<span>4G LTE</span>
					</div>
				</div>

				<div class="space-y-5 pt-4">
					<div class="flex justify-between items-center">
						<div>
							<p class="text-xs text-slate-500">Remaining Budget</p>
							<p class="text-2xl font-bold text-white tracking-wide">K 16,000</p>
						</div>
						<div class="text-right">
							<p class="text-[10px] text-slate-500">Total Spent</p>
							<p class="text-sm font-semibold text-rose-400">K 4,000</p>
						</div>
					</div>

					<div class="w-full h-2 bg-slate-900 rounded-full overflow-hidden">
						<div class="w-4/5 h-full bg-gradient-to-r from-emerald-500 to-teal-400 rounded-full" />
					</div>

					<div class="grid grid-cols-2 gap-3">
						<div class="p-3 bg-slate-900/60 border border-slate-800/80 rounded-2xl">
							<p class="text-[10px] text-slate-500 mb-1">Total Bought</p>
							<p class="text-base font-bold text-white">1.0g</p>
						</div>
						<div class="p-3 bg-slate-900/60 border border-slate-800/80 rounded-2xl">
							<p class="text-[10px] text-slate-500 mb-1">Sessions</p>
							<p class="text-base font-bold text-white">1 Active</p>
						</div>
					</div>

					<div class="space-y-2">
						<p class="text-xs font-semibold text-slate-400">Recent Logs</p>
						<div class="p-3 bg-slate-900/40 border border-slate-800/50 rounded-xl flex items-center justify-between">
							<div class="flex items-center gap-2.5">
								<div class="w-7 h-7 rounded-lg bg-purple-500/10 flex items-center justify-center">
									<Flame class="w-4 h-4 text-purple-400" />
								</div>
								<div>
									<p class="text-xs font-medium text-white">Smoked Popcorn</p>
									<p class="text-[10px] text-slate-500">05:43 • Wake & Bake</p>
								</div>
							</div>
							<span class="text-[11px] font-medium text-slate-400">May 21</span>
						</div>
					</div>
				</div>

				<div class="mt-6 p-3 bg-slate-900 border border-slate-800 rounded-2xl space-y-2.5">
					<div class="flex justify-between items-center text-[11px]">
						<span class="text-slate-400">What did you smoke?</span>
						<span class="text-emerald-400 font-medium">Popcorn (K 4,000/g)</span>
					</div>
					<div class="w-full py-2 bg-purple-600 rounded-xl text-center text-xs font-bold text-white shadow-lg shadow-purple-600/20">
						🔥 Log Session Now
					</div>
				</div>
			</div>
		</div>
	</section>

	<hr class="border-slate-900 container mx-auto px-6" />

	<section class="container mx-auto px-6 py-24 relative z-10">
		<div class="text-center max-w-3xl mx-auto mb-16 space-y-4">
			<h2 class="text-3xl md:text-4xl font-bold text-white tracking-tight">
				Designed to build healthy tracking habits
			</h2>
			<p class="text-slate-400 text-base">
				Whether you want to optimize your tolerance breaks, monitor your financial investment, or safely categorize local flowers, BudTracker has you covered.
			</p>
		</div>

		<div class="grid lg:grid-cols-12 gap-8 items-stretch">
			<div class="lg:col-span-5 flex flex-col justify-center gap-4">
				{#each features as feature}
					<button
						class="w-full p-5 rounded-2xl border text-left transition-all duration-300 relative overflow-hidden group {activeTab === feature.id ? 'bg-slate-900/90 border-slate-700 shadow-xl' : 'bg-transparent border-transparent hover:bg-slate-900/40'}"
						onclick={() => activeTab = feature.id}
					>
						<div class="flex items-start gap-4">
							<div class="p-3 rounded-xl transition-all duration-300 {feature.bg} {feature.color}">
								<svelte:component this={feature.icon} class="w-6 h-6" />
							</div>
							<div class="space-y-1">
								<h3 class="font-semibold text-base text-white group-hover:text-emerald-400 transition-colors">
									{feature.title}
								</h3>
								<p class="text-sm text-slate-400 leading-relaxed">
									{feature.description}
								</p>
							</div>
						</div>
					</button>
				{/each}
			</div>

			<div class="lg:col-span-7 bg-slate-950/40 border border-slate-900 rounded-3xl p-8 flex flex-col justify-center items-center relative overflow-hidden min-h-[360px]">
				{#if activeTab === 'track'}
					<div class="w-full max-w-md space-y-4 text-center" in:fade={{ duration: 300 }}>
						<div class="inline-flex p-4 rounded-full bg-purple-500/10 text-purple-400 mb-2">
							<Layers class="w-8 h-8" />
						</div>
						<h4 class="text-lg font-semibold text-white">Your Personal Flower Dispenser Matrix</h4>
						<p class="text-sm text-slate-400">
							Manage your native stash directly inside the interface. Instantly toggle prices to check real-time value changes instantly across your dashboard view.
						</p>
						<div class="bg-slate-900/90 border border-slate-800 rounded-xl p-3 text-left max-w-xs mx-auto text-xs space-y-2">
							<div class="flex justify-between text-slate-300"><span>🌿 Sour Peach</span> <span class="text-emerald-400">K 4,000/g</span></div>
							<div class="flex justify-between text-slate-300"><span>🌿 Blue Diesel</span> <span class="text-emerald-400">K 4,000/g</span></div>
							<div class="flex justify-between text-slate-300"><span>🌿 White Russian</span> <span class="text-emerald-400">K 4,000/g</span></div>
						</div>
					</div>
				{:else if activeTab === 'budget'}
					<div class="w-full max-w-md space-y-4 text-center" in:fade={{ duration: 300 }}>
						<div class="inline-flex p-4 rounded-full bg-emerald-500/10 text-emerald-400 mb-2">
							<Wallet class="w-8 h-8" />
						</div>
						<h4 class="text-lg font-semibold text-white">Strict Budgetary Tracking Caps</h4>
						<p class="text-sm text-slate-400">
							Protect your real wallet investments. Set thresholds that change dynamically when recording entries, ensuring complete transparency with your income stream allocations.
						</p>
					</div>
				{:else if activeTab === 'insights'}
					<div class="w-full max-w-md space-y-4 text-center" in:fade={{ duration: 300 }}>
						<div class="inline-flex p-4 rounded-full bg-cyan-500/10 text-cyan-400 mb-2">
							<Sparkles class="w-8 h-8" />
						</div>
						<h4 class="text-lg font-semibold text-white">Advanced Generative Metric Summaries</h4>
						<p class="text-sm text-slate-400">
							The AI Budtender looks deep through your timeline history. It flags if streaks climb dangerously fast or highlights when successful tolerance steps protect your system.
						</p>
					</div>
				{/if}
			</div>
		</div>
	</section>

	<section id="calculator" class="py-20 bg-gradient-to-b from-transparent to-slate-950/60 border-t border-b border-slate-900 relative">
		<div class="container mx-auto px-6 max-w-4xl">
			<div class="text-center mb-12 space-y-3">
				<div class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-md bg-purple-500/10 border border-purple-500/20 text-purple-400 text-xs font-semibold">
					<TrendingUp class="w-3.5 h-3.5" /> Budget Optimizer Widget
				</div>
				<h2 class="text-3xl font-bold text-white tracking-tight">Calculate Your Bud Investment</h2>
				<p class="text-sm text-slate-400">See real monthly & yearly metrics to see exactly how much cash you drop on flower.</p>
			</div>

			<div class="grid md:grid-cols-2 gap-8 items-center bg-[#0E1322] border border-slate-800 rounded-3xl p-8 shadow-2xl">
				<div class="space-y-6">
					<div class="space-y-2">
						<div class="flex justify-between items-center text-sm">
							<span class="text-slate-400 font-medium">Weekly Consumption (Grams)</span>
							<span class="text-emerald-400 font-bold text-base">{weeklyGrams}g</span>
						</div>
						<input 
							type="range" 
							min="1" 
							max="25" 
							bind:value={weeklyGrams} 
							class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-emerald-500"
						/>
					</div>

					<div class="space-y-2">
						<div class="flex justify-between items-center text-sm">
							<span class="text-slate-400 font-medium">Average Market Price per Gram</span>
							<span class="text-emerald-400 font-bold text-base">K {pricePerGram.toLocaleString()}</span>
						</div>
						<input 
							type="range" 
							min="1000" 
							max="15000" 
							step="500"
							bind:value={pricePerGram} 
							class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-emerald-500"
						/>
					</div>
				</div>

				<div class="p-6 rounded-2xl bg-slate-900/50 border border-slate-800 space-y-4">
					<div>
						<p class="text-xs text-slate-400 uppercase tracking-wider font-semibold">Monthly Investment Projection</p>
						<p class="text-3xl font-extrabold text-white tracking-tight mt-1">K {monthlySpend.toLocaleString()}</p>
					</div>
					<hr class="border-slate-800" />
					<div>
						<p class="text-xs text-slate-400 uppercase tracking-wider font-semibold">Yearly Total Footprint</p>
						<p class="text-xl font-bold text-purple-400 tracking-tight mt-1">K {yearlySpend.toLocaleString()}</p>
					</div>
					<p class="text-[11px] text-slate-500 italic leading-snug">
						💡 Setting a smart cap inside BudTracker could save you over 20% on these baseline market totals!
					</p>
				</div>
			</div>
		</div>
	</section>

	<section id="download" class="container mx-auto px-6 py-24 text-center relative max-w-4xl">
		<div class="absolute inset-0 bg-emerald-500/5 rounded-3xl blur-3xl pointer-events-none transform translate-y-10" />
		
		<div class="bg-gradient-to-r from-slate-900 via-[#0E1322] to-slate-900 border border-slate-800 rounded-3xl p-12 space-y-8 shadow-2xl relative z-10">
			<div class="w-14 h-14 rounded-2xl bg-gradient-to-tr from-emerald-500 to-teal-400 flex items-center justify-center shadow-xl shadow-emerald-500/10 mx-auto">
				<Leaf class="w-7 h-7 text-[#0B0F19] stroke-[2.5]" />
			</div>
			
			<div class="space-y-3 max-w-xl mx-auto">
				<h2 class="text-3xl md:text-4xl font-extrabold text-white tracking-tight">Ready for a mindful tracking journey?</h2>
				<p class="text-slate-400 text-sm md:text-base leading-relaxed">
					Get access to beautiful dashboards, automated streak calculations, secure local-first records, and smarter budgeting tools.
				</p>
			</div>

			<div class="flex flex-wrap gap-4 justify-center items-center pt-4">
				<button class="px-6 py-3.5 rounded-xl bg-white text-slate-950 font-semibold hover:bg-slate-100 transition-all flex items-center gap-3 shadow-xl text-sm">
					<a href="/Bud Tracker (1).apk" download>Download APK Securely</a>
				</button>
				<button class="px-6 py-3.5 rounded-xl bg-slate-900 border border-slate-800 hover:border-slate-700 font-semibold text-slate-200 transition-all text-sm">
					<a href="/Bud Tracker (1).apk" download>Web App PWA Link</a>
				</button>
			</div>

			<div class="pt-6 flex justify-center gap-6 text-xs text-slate-500">
				<span class="flex items-center gap-1.5"><CheckCircle2 class="w-3.5 h-3.5 text-emerald-400" /> Free local backups</span>
				<span class="flex items-center gap-1.5"><CheckCircle2 class="w-3.5 h-3.5 text-emerald-400" /> No email signup needed</span>
			</div>
		</div>
	</section>

	<footer class="container mx-auto px-6 py-8 border-t border-slate-900 text-center relative z-10 text-xs text-slate-500">
		<p>© 2026 BudTracker app system. Designed with love for local flowers and smart spenders.</p>
	</footer>
</div>

<style>
	input[type='range']::-webkit-slider-thumb {
		box-shadow: 0px 0px 10px rgba(16, 185, 129, 0.4);
	}
</style>