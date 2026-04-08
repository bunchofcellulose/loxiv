<script lang="ts">
	import SvelteSeo from 'svelte-seo';
	import { Book, Wrench, Users } from 'lucide-svelte';

	const resourceCategories = [
		{
			title: "Training Guides & Textbooks",
			description: "Comprehensive guides designed specifically to teach the logic of linguistics puzzles.",
			icon: Book,
			iconColor: "text-indigo-500",
			links: [
				{ 
					name: "Linguistics Olympiad: Training Guide", 
					url: "https://langsci-press.org/catalog/book/420", 
					desc: "An open-access textbook covering the most common types of problems found in the IOL." 
				},
				{ 
					name: "UKLO Round 2 Prep Guide", 
					url: "https://www.uklo.org/wp-content/uploads/2022/05/UKLO-Round-2-Preparation.pdf", 
					desc: "Advanced techniques and strategies from the UK Linguistics Olympiad committee." 
				},
				{ 
					name: "Onling Resources", 
					url: "https://onling.org/resources/", 
					desc: "A massive library of practice problems and categorized training materials." 
				},
				{ 
					name: "PLO Resources", 
					url: "https://ltrc.iiit.ac.in/plo/resources.html", 
					desc: "Curated learning materials provided by the Panini Linguistics Olympiad team." 
				}
			]
		},
		{
			title: "Tools & Reference",
			description: "Essential tools for decoding and analyzing linguistic data.",
			icon: Wrench,
			iconColor: "text-emerald-500",
			links: [
				{ 
					name: "Interactive IPA Chart", 
					url: "https://www.ipachart.com/", 
					desc: "The complete International Phonetic Alphabet with audio samples for every character." 
				},
				{ 
					name: "UKLO Official Site", 
					url: "https://www.uklo.org/", 
					desc: "Main portal for the UK Linguistics Olympiad—access past papers and competition news." 
				}
			]
		},
		{
			title: "Communities & Discord",
			description: "Join the conversation, ask for hints, and meet fellow olympiad enthusiasts.",
			icon: Users,
			iconColor: "text-rose-500",
			links: [
				{ 
					name: "Linguistics Olympiad Discord", 
					url: "https://discord.gg/EaYmbmEar8", 
					desc: "The central global hub for IOL and general linguistics puzzle discussion." 
				},
				{ 
					name: "NACLO Discord Server", 
					url: "https://discord.gg/e87PaRK7Bm", 
					desc: "Community server specifically for the North American Computational Linguistics Open." 
				}
			]
		}
	];
</script>

<SvelteSeo
	title="Resources"
	description="Curated materials for Linguistics Olympiad preparation."
	keywords="linguistics olympiad, training guides, resources, IPA, discord, community"
/>

<div class="mx-auto max-w-3xl px-4 py-10 sm:px-6">
	<!-- Page Header -->
	<div class="mb-10">
		<h1 class="text-3xl font-extrabold tracking-tight text-foreground">Resources</h1>
		<p class="mt-1.5 max-w-xl text-sm text-muted-foreground">
			Curated materials for Linguistics Olympiad preparation.
		</p>
	</div>

	<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
		{#each resourceCategories as category, idx}
			<section class={idx === 0 ? 'md:col-span-2' : ''}>
				<!-- Section heading -->
				<div class="mb-4 flex items-center gap-3">
					<svelte:component this={category.icon} class="h-6 w-6 {category.iconColor}" />
					<h2 class="text-base font-bold tracking-tight text-foreground">{category.title}</h2>
				</div>

				<!-- Link list -->
				<div class="divide-y divide-border overflow-hidden rounded-2xl border border-border">
					{#each category.links as link}
						<a
							href={link.url}
							target="_blank"
							rel="noopener noreferrer"
							class="group flex items-center justify-between gap-4 bg-card px-5 py-4 transition-colors hover:bg-muted/60"
						>
							<div class="min-w-0">
								<p class="text-sm font-semibold text-foreground transition-colors group-hover:text-primary">
									{link.name}
								</p>
								<p class="mt-0.5 text-xs leading-relaxed text-muted-foreground">
									{link.desc}
								</p>
							</div>
							<svg 
								class="-rotate-45 h-4 w-4 shrink-0 text-muted-foreground/50 transition-colors group-hover:text-primary" 
								fill="none" 
								stroke="currentColor" 
								viewBox="0 0 24 24"
							>
								<path 
									stroke-linecap="round" 
									stroke-linejoin="round" 
									stroke-width="2" 
									d="M14 5l7 7m0 0l-7 7m7-7H3"
								/>
							</svg>
						</a>
					{/each}
				</div>
			</section>
		{/each}
	</div>

	<p class="mt-10 text-center text-xs text-muted-foreground">
		Have a resource to suggest? 
		<a href="mailto:lotrackerdev@gmail.com" class="underline hover:text-foreground">Email us</a> 
		or ping us on Discord.
	</p>
</div>
