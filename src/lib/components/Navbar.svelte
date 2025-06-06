<script lang="ts">
	import { is } from 'drizzle-orm';
	import { blur, crossfade, draw, fade, fly, scale, slide } from 'svelte/transition';

	let mainHoveredLinkIndex = null;
	let secondaryHoveredLinkIndex = null;
	let isMobileMenuOpen = false;

	let mainLinks = [
		{ href: '/', label: 'Main Page' },
		{ href: '/editor', label: 'Note Editor' },
		{ href: '/list', label: 'Note List' }
	];
	let secondaryLinks = [
		{ href: '/login', label: 'Login' },
		{ href: '/register', label: 'Register' }
	];
</script>

<nav class="bg-gradient-to-r from-black to-gray-800 text-white shadow-lg">
	<div class="container mx-auto flex items-center justify-between px-6 py-4">
		<div class="flex items-center gap-4">
			<a href="/" class="text-4xl font-bold tracking-tight">Notes</a>
		</div>
		<div class="hidden items-center gap-7 md:flex">
			{#each mainLinks as link, index}
				<a
					href={link.href}
					class="navbar-item transition-opacity duration-600"
					style="opacity: {mainHoveredLinkIndex === null
						? 1
						: mainHoveredLinkIndex === index
							? 1
							: 0.3};"
					on:mouseenter={() => (mainHoveredLinkIndex = index)}
					on:mouseleave={() => (mainHoveredLinkIndex = null)}
				>
					{link.label}
				</a>
			{/each}
		</div>
		<div class="hidden items-center gap-7 md:flex">
			{#each secondaryLinks as link, index}
				<a
					href={link.href}
					class="navbar-item transition-opacity duration-600 border border-amber-50 rounded-xl px-3 py-1"
					style="opacity: {secondaryHoveredLinkIndex === null
						? 1
						: secondaryHoveredLinkIndex === index
							? 1
							: 0.3};"
					on:mouseenter={() => (secondaryHoveredLinkIndex = index)}
					on:mouseleave={() => (secondaryHoveredLinkIndex = null)}
				>
					{link.label}
				</a>
			{/each}
		</div>
		<div class="flex items-center md:hidden">
			<button on:click={() => (isMobileMenuOpen = !isMobileMenuOpen)} class="focus:outline-none">
				<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					{#if isMobileMenuOpen}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					{:else}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					{/if}
				</svg>
			</button>
		</div>
	</div>
	{#if isMobileMenuOpen}
		<div class="space-y-2 px-6 pb-4 md:hidden" transition:slide={{ duration: 600 }}>
			{#each mainLinks as link}
				<a href={link.href} class="block rounded px-4 py-2 duration-500 hover:bg-gray-500">
					{link.label}
				</a>
			{/each}
			<a href="/login" class="block rounded px-4 py-2 duration-500 hover:bg-gray-500">Login</a>
			<a href="/register" class="block rounded px-4 py-2 duration-500 hover:bg-gray-500">Register</a
			>
		</div>
	{/if}
</nav>

<style>
	nav {
		font-family: 'Manrope', sans-serif;
		font-size: large;
	}
</style>
