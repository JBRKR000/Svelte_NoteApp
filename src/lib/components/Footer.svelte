<script lang="ts">
    import { is } from 'drizzle-orm';

	let date = new Date();
	let year = date.getFullYear();

    let hoveredIconIndex = null;
    let myIcons = [
    {name: 'github', class: 'bi-github text-2xl md:text-3xl', href: 'https://github.com/JBRKR000', label: 'GitHub'},
    {name: 'linkedin', class: 'bi-linkedin text-2xl md:text-3xl', href:'https://linkedin.com', label: 'LinkedIn'},
    {name: 'instagram', class: 'bi-instagram text-2xl md:text-3xl', href: 'https://instagram.com', label: 'Instagram'},
    {name: 'envelope', class: 'bi-envelope text-2xl md:text-3xl', href:'mailto:someone@example.com', label: 'Email'}
    ]
</script>

<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
</svelte:head>

<footer>
	<div class="relative bg-gradient-to-r from-black to-gray-800 py-6 text-emerald-50 shadow-lg">
		<div class="container mx-auto px-4">
			<div class="flex flex-col items-center md:flex-row md:justify-center relative">

				<div class="text-center">
					<p class="text-sm">© {year} Notes App. All rights reserved.</p>
					<p class="mt-2 text-xs">
						Built by <a href="https://github.com/JBRKR000">JBRKR</a> with Svelte
					</p>
				</div>
				<div class="mt-4 md:mt-0 md:absolute md:right-4 md:top-1/2 md:-translate-y-1/2 flex space-x-5">
					{#each myIcons as myIcon, index}
                        <a href={myIcon.href} target="_blank" aria-label={myIcon.label}
                        class="transition-opacity duration-600"
                        style="opacity: {hoveredIconIndex === null
						? 1
						: hoveredIconIndex === index
							? 1
							: 0.3};"
                            on:mouseenter={() => (hoveredIconIndex = index)}
					        on:mouseleave={() => (hoveredIconIndex = null)}
                        >
                            <i class={myIcon.class}></i>
                        </a>
                    {/each}
				</div>

			</div>
		</div>
	</div>
</footer>

<style>
	footer {
		font-family: 'Manrope', sans-serif;
		font-weight: 200;
	}
</style>
