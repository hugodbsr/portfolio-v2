<script lang="ts">
	import './layout.css';
	import favicon from '#lib/assets/favicon.svg';
	import type { LayoutProps } from './$types';
	import NavButton from '#lib/components/NavButton.svelte';

	let { children }: LayoutProps = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="flex w-full flex-col justify-center">
	<h1 class="mt-3 flex flex-row justify-center">Hugo DEBUYSER</h1>

	<div class="mt-3 flex w-full flex-row justify-center gap-5">
		<NavButton link="/" name="Présentation"></NavButton>
		<NavButton link="/background" name="Parcours"></NavButton>
		<NavButton link="/skills" name="Compétences"></NavButton>
		<NavButton link="/projects" name="Projets"></NavButton>
		<NavButton link="https://github.com/hugodbsr" name="Github" external></NavButton>
	</div>
</div>

{@render children()}
