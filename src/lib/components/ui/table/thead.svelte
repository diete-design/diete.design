<script lang="ts">
	import type { HTMLAttributes } from 'svelte/elements'
	let { children }: HTMLAttributes<HTMLElement> = $props()
</script>

<thead>
	{#if children}
		{@render children()}
	{/if}
</thead>

<style lang="postcss">
	thead {
		appearance: none;
		border-bottom: 1px solid var(--colors-ultra-high);
	}
</style>
