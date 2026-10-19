<script lang="ts">
	interface Props {
		name: string;
		link: string;
		external?: boolean;
	}
	let { name, link, external = false } = $props();
</script>

<a
	class="rounded-xl border-2 border-l-gray-700 px-5 py-2"
	href={link}
	target={external ? '_blank' : undefined}
	rel={external ? 'noopener noreferrer' : undefined}
	>{name}
</a>
