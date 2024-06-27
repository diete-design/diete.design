<script lang="ts">
	import MenuItem from '$lib/components/ui/menu/menu-item.svelte'
	import MenuTitle from '$lib/components/ui/menu/menu-title.svelte'
	import Typography from '$lib/components/ui/typography.svelte'
	import Button from '$lib/components/ui/button.svelte'
	import { Light, SidePanelCloseFilled, SidePanelOpenFilled, Launch } from 'carbon-icons-svelte'
	import '../app.pcss'
	import '../diete.css'
	import Dropdown from '$lib/components/custom/dropdown.svelte'
	import ThemeSelector from '$lib/components/custom/theme-selector.svelte'
	import { page } from '$app/stores'

	let { children } = $props()

	let isMenuOpen = $state(false)
	let innerWidth: number | undefined = $state()

	const mobileWidth = 700
	const menuAlwaysOpen = true

	const menu: { [title: string]: { [path: string]: string } } = {
		Diète: {
			'/': 'Intro',
			'/build': 'Build with Diète',
			'/colors': 'CSS colors',
			'https://github.com/diete-design/diete.design': 'Github',
		},
		Components: {
			'/components/badge': 'Badge',
			'/components/button': 'Button',
			'/components/divider': 'Divider',
			'/components/checkbox': 'Checkbox',
			'/components/input': 'Input',
			'/components/loader': 'Loader',
			'/components/menu': 'Menu',
			'/components/progress': 'Progress bar',
			'/components/radio': 'Radio',
			'/components/select': 'Select',
			'/components/slider': 'Slider',
			'/components/switch': 'Switch',
			'/components/table': 'Table',
			'/components/textarea': 'Textarea',
			'/components/tooltip': 'Tooltip',
			'/components/typography': 'Typography',
		},
	}

	const inverseMenu = Object.fromEntries(
		Object.keys(menu).reduce(
			(r, key) => r.concat(Object.entries(menu[key])),
			[] as [string, string][],
		),
	)

	// for some reason using $page is now an error
	// https://github.com/sveltejs/eslint-plugin-svelte/issues/652#issuecomment-2028495896

	// eslint-disable-next-line svelte/valid-compile
	const pathname = $derived($page.url.pathname)
	let menuTitleIsOpen = $state(makeMenuItemOpenMapping())

	const title = $derived(
		'Diète design system' + (inverseMenu[pathname] ? ` - ${inverseMenu[pathname]}` : ''),
	)

	$effect(() => {
		pathname
		menuTitleIsOpen = makeMenuItemOpenMapping()
	})

	function isActivePage(path: string) {
		return path === pathname
	}

	function isActivePageInMenu(title: string) {
		return Object.keys(menu[title] || {}).some((path) => isActivePage(path))
	}

	function makeMenuItemOpenMapping() {
		const menuOpen: { [title: string]: boolean } = {}

		Object.keys(menu).forEach(
			(menu) => (menuOpen[menu] = menuAlwaysOpen || isActivePageInMenu(menu)),
		)

		return menuOpen
	}

	function isExternalLink(link: string) {
		return link.startsWith('https://')
	}

	function menuOnClick() {
		// close the menu after a click on mobile
		if (innerWidth && innerWidth < mobileWidth) {
			isMenuOpen = false
		}
	}
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<svelte:window bind:innerWidth />

<div class="menu-button-container">
	<Button variant="solid" onclick={() => (isMenuOpen = !isMenuOpen)}>
		{#if isMenuOpen}
			<SidePanelCloseFilled size={24} />
		{:else}
			<SidePanelOpenFilled size={24} />
		{/if}
	</Button>
</div>

<div class="dark-mode-button-container">
	{#snippet button()}
		<Light size={24} />
	{/snippet}
	<Dropdown left {button}>
		<ThemeSelector />
	</Dropdown>
</div>
<div class="container">
	<div class="menu-{isMenuOpen ? 'open' : 'closed'}-placeholder">
		{#if isMenuOpen}
			<div class="menu-header"></div>
			<div class="menu">
				{#each Object.entries(menu) as [title, pages]}
					{#snippet content()}
						{title}
					{/snippet}
					<MenuTitle {content} bold bind:open={menuTitleIsOpen[title]}>
						{#each Object.entries(pages) as [path, title]}
							<MenuItem
								active={isActivePage(path)}
								href={path}
								onclick={menuOnClick}
								target={isExternalLink(path) ? '_blank' : undefined}
								>{#if isExternalLink(path)}
									<Launch size={24} />
								{/if}{title}</MenuItem
							>
						{/each}
					</MenuTitle>
				{/each}
			</div>
		{/if}
	</div>
	<div class="right">
		<div class="header"></div>

		<div class="content-container">
			<div class="content">
				{#if children}
					{@render children()}
				{/if}

				<section id="footer">
					<Typography>
						Source code is available on <a href="https://github.com/diete-design/diete.design"
							>Github</a
						>.
					</Typography>
				</section>
			</div>
		</div>
	</div>
</div>

<style lang="postcss">
	.container {
		--header-size: 80px;
		--sidebar-size: 238px;
		--max-content-width: 1136px;

		display: flex;
		flex-direction: row;
	}
	.menu-button-container {
		position: fixed;
		top: var(--padding);
		left: var(--padding);
		z-index: 100;
	}
	.dark-mode-button-container {
		position: fixed;
		top: var(--padding);
		right: var(--padding);
		z-index: 100;
	}
	.menu {
		position: fixed;
		top: var(--header-size);
		bottom: 0px;
		left: 0px;
		border-right: 1px solid var(--colors-low);
		background-color: var(--colors-ultra-low);
		padding: var(--padding);
		width: var(--sidebar-size);
		overflow-x: hidden;
		overflow-y: auto;
	}
	.menu-header {
		position: fixed;
		top: 0px;
		left: 0px;
		border-right: var(--colors-low) 1px solid;
		background-color: var(--colors-ultra-low);
		min-width: var(--sidebar-size);
		height: var(--header-size);
	}
	.menu-open-placeholder {
		transition:
			background-color 0.25s,
			min-width 0.25s;
		margin-top: var(--header-size);
		background-color: var(--colors-low);
		min-width: var(--sidebar-size);
	}
	.menu-closed-placeholder {
		transition:
			background-color 0.25s,
			min-width 0.25s;
		background-color: var(--colors-base);
		min-width: 0px;
	}
	@media only screen and (max-device-width: 700px) {
		.menu-open-placeholder {
			position: absolute;
			top: 0px;
			bottom: 0px;
			left: 0px;
			z-index: 1;
			transition: none;
			background-color: var(--colors-low);
		}
		.menu-closed-placeholder {
			transition: none;
			background-color: var(--colors-base);
			min-width: 0px;
		}
	}
	.right {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
	}
	.content-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
	}
	.content {
		flex: 1;
		margin-bottom: var(--header-size);
		padding: 0 var(--padding);
		max-width: var(--max-content-width);
	}
	.header {
		height: var(--header-size);
	}
</style>
