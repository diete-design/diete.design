<script lang="ts">
	import type { HTMLAttributes } from 'svelte/elements'
	let { children, ...restProps }: HTMLAttributes<HTMLElement> = $props()
</script>

<tbody {...restProps}>
	{#if children}
		{@render children()}
	{/if}
</tbody>

<style lang="postcss">
	tbody {
		appearance: none;
	}
</style>
