<script lang="ts">
	import './layout.css';
	import favicon from '#lib/assets/favicon.svg';
	import type { LayoutProps } from './$types';
	import type { RouteId } from '$app/types';
	import NavButton from '#lib/components/NavButton.svelte';

	let { children }: LayoutProps = $props();

	const internalNavItems: { name: string; link: RouteId }[] = [
		{ name: 'Présentation', link: '/' },
		{ name: 'Parcours', link: '/background' },
		{ name: 'Compétences', link: '/skills' },
		{ name: 'Projets', link: '/projects' }
	];
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Portfolio • Hugo DEBUYSER</title>
</svelte:head>

<header
	class="top-0 z-10 w-full animate-header-banner bg-secondary bg-[url('https://www.transparenttextures.com/patterns/dark-stripes.png')] py-2 text-center text-[0.8rem]"
>
	<h1 class="my-2 translate-y-2 -rotate-[0.2deg] animate-fade-in-delayed text-[2em] font-bold">
		Hugo DEBUYSER
	</h1>
</header>

<nav
	aria-label="Navigation principale"
	class="relative z-1 flex w-full translate-y-5 -rotate-[0.2deg] animate-fade-in-delayed flex-wrap items-center justify-center text-[1.4rem]"
>
	{#each internalNavItems as item (item.link)}
		<NavButton link={item.link} name={item.name} />
	{/each}
	<NavButton link="https://github.com/hugodbsr" name="Github" external />
</nav>

<main class="flex-1 animate-fade-in-delayed p-5">
	{@render children()}
</main>
