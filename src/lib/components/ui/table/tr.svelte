<script lang="ts">
	import type { HTMLAttributes } from 'svelte/elements'
	interface Props extends HTMLAttributes<HTMLElement> {
		active?: boolean
	}
	let { active, children, ...restProps }: Props = $props()
</script>

<tr {...restProps} class:active>
	{#if children}
		{@render children()}
	{/if}
</tr>

<style lang="postcss">
	tr {
		appearance: none;
		border-bottom: 1px solid var(--colors-low);
		&:has(th) {
			border-bottom: 1px solid var(--colors-ultra-high);
		}
		&:last-child {
			width: 1rem;
		}
		&.active:not(:first-child) {
			background-color: var(--colors-low);
		}
	}
</style>
