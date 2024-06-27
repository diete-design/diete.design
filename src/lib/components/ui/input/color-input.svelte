<script lang="ts">
	import { ColorPalette } from 'carbon-icons-svelte'
	import Button from '../button.svelte'
	import Input, { type Props } from './input.svelte'
	import type { HTMLInputAttributes } from 'svelte/elements'
	let {
		dimension,
		disabled,
		variant = 'outline',
		...restProps
	}: Props & HTMLInputAttributes = $props()
	let size: 16 | 24 | 32 = $derived(dimension === 'large' ? 32 : dimension === 'small' ? 16 : 24)
	let color = $state()
	let colorInput: HTMLInputElement
</script>

{#snippet buttons()}
	<Button
		{dimension}
		{disabled}
		onclick={() => colorInput.click()}
		variant={variant === 'outline' ? 'secondary' : 'solid'}
	>
		<div class="relative">
			<div class="palette-icon">
				<ColorPalette {size} />
			</div>
			<input type="color" bind:value={color} bind:this={colorInput} />
		</div>
	</Button>
{/snippet}

<Input bind:value={color} {dimension} {disabled} {variant} type="text" {buttons} {...restProps} />

<style lang="postcss">
	.relative {
		display: flex;
		position: relative;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100%;
	}
	input[type='color'] {
		appearance: none;
		visibility: hidden;
		cursor: pointer;
		border: none;
		background-color: var(--colors-top);
		padding: 0;
		width: 100%;
		height: 100%;
	}
	input[type='color']::-webkit-color-swatch-wrapper {
		box-sizing: border-box;
		margin: 0;
		border: 0;
		padding: 0;
	}
	input[type='color']::-webkit-color-swatch,
	input[type='color']::-moz-color-swatch {
		margin: 0;
		outline: 0;
		border: none;
		border-radius: 0 var(--border-radius) var(--border-radius) 0;
		padding: 0;
		width: 100%;
		height: 100%;
	}
	.palette-icon {
		position: absolute;
		transform: translate(-50%, -50%);
		inset: 50% auto auto 50%;
		line-height: 0;
		fill: var(--colors-top);
	}
</style>
