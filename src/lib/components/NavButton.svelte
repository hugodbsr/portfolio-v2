<script lang="ts">
	import { resolve } from '$app/paths';
	import { page } from '$app/state';
	import type { RouteId } from '$app/types';

	interface InternalProps {
		name: string;
		link: RouteId;
		external?: false;
	}

	interface ExternalProps {
		name: string;
		link: `http://${string}` | `https://${string}`;
		external: true;
	}

	type Props = InternalProps | ExternalProps;

	let { name, link, external = false }: Props = $props();

	let rotation = $state(0);
	const isActive = $derived(!external && page.url.pathname === link);
	const resolvedHref = $derived(external ? link : resolve(link as RouteId));

	function handleMouseEnter() {
		rotation = Math.random() * 5 - 2.5;
	}

	function handleMouseLeave() {
		rotation = 0;
	}
</script>

<!-- eslint-disable svelte/no-navigation-without-resolve -->
<a
	class="relative mx-3 my-1.5 inline-block rounded-[6px] border-[3px] border-border bg-diagonal-button px-4 py-2.5 text-[1.4rem] font-bold whitespace-nowrap text-foreground opacity-85 shadow-button transition-[transform,background-position,border-color,opacity] duration-300 text-shadow-button hover:bg-top-right hover:opacity-100 md:mx-6"
	class:bg-top-right={isActive}
	class:border-secondary={isActive}
	class:opacity-100={isActive}
	style:transform="rotate({rotation}deg)"
	onmouseenter={handleMouseEnter}
	onmouseleave={handleMouseLeave}
	href={resolvedHref}
	aria-current={isActive ? 'page' : undefined}
	target={external ? '_blank' : undefined}
	rel={external ? 'noopener noreferrer' : undefined}
>
	{name}
</a>
