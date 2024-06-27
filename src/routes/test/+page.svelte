<script lang="ts">
	import {
		Checkmark,
		ArrowRight,
		CheckmarkFilled,
		NotificationNew,
		ThumbsUpFilled,
		ThumbsDown,
		Error,
		ChevronDown,
	} from 'carbon-icons-svelte'

	import Button from '$lib/components/ui/button.svelte'
	import Checkbox from '$lib/components/ui/checkbox.svelte'
	import Input from '$lib/components/ui/input/input.svelte'
	import Radio from '$lib/components/ui/radio-button/radio.svelte'
	import Typography from '$lib/components/ui/typography.svelte'
	import Switch from '$lib/components/ui/switch.svelte'
	import Select from '$lib/components/ui/select/select.svelte'
	import Option from '$lib/components/ui/select/option.svelte'
	import MenuTitle from '$lib/components/ui/menu/menu-title.svelte'
	import MenuItem from '$lib/components/ui/menu/menu-item.svelte'
	import RadioGroup from '$lib/components/ui/radio-button/radio-group.svelte'
	import Slider from '$lib/components/ui/slider.svelte'
	import RangeSlider from '$lib/components/ui/range-slider.svelte'
	import Textarea from '$lib/components/ui/textarea.svelte'
	import Badge from '$lib/components/ui/badge.svelte'
	import Loader from '$lib/components/ui/loader.svelte'
	import ProgressBar from '$lib/components/ui/progress.svelte'
	import NumberInput from '$lib/components/ui/input/number-input.svelte'
	import SearchInput from '$lib/components/ui/input/search-input.svelte'
	import ColorInput from '$lib/components/ui/input/color-input.svelte'
	import DateInput from '$lib/components/ui/input/date-input.svelte'
	import Table from '$lib/components/ui/table/table.svelte'
	import Tr from '$lib/components/ui/table/tr.svelte'
	import Th from '$lib/components/ui/table/th.svelte'
	import Td from '$lib/components/ui/table/td.svelte'
	import Thead from '$lib/components/ui/table/thead.svelte'
	import Tbody from '$lib/components/ui/table/tbody.svelte'

	let selected: boolean[] = $state([])
	let selectedCount = $state(0)
	let selectionAll = $state(false)
	function selectAll() {
		const allChecked = selectedCount === selected.length
		selected = selected.map(() => !allChecked)
		selectedCount = allChecked ? 0 : selected.length
	}
	function toggleSelection(index: number) {
		selected[index] = !selected[index]
		selectedCount += selected[index] ? 1 : -1
	}
	$effect(() => {
		const row = document.querySelectorAll('.with-checkbox')
		selected = new Array(row.length).fill(false)
	})
	$effect(() => {
		if (selectedCount === selected.length) {
			selectionAll = true
		} else {
			selectionAll = false
		}
	})
</script>

<div class="page-wrapper">
	<Typography variant="h1">A design system for purists</Typography>
	<Typography variant="default" element="p">
		Radically minimal UI components, that you can copy directly into your project. Diète is for
		uncompromising, free-spirited app makers who want to remain independent.
	</Typography>

	<section id="button">
		<Typography variant="h1">Button</Typography>
		<div class="row">
			<div class="col">
				<Button>Strong</Button>
				<Button hover>Strong hover</Button>
				<Button active>Strong active</Button>
				<Button focus>Strong focus</Button>
				<Button focus active>Strong focus active</Button>
				<Button disabled>Strong disabled</Button>
			</div>
			<div class="col">
				<Button><Checkmark size={24} /></Button>
				<Button hover><Checkmark size={24} /></Button>
				<Button active><Checkmark size={24} /></Button>
				<Button focus><Checkmark size={24} /></Button>
				<Button focus active><Checkmark size={24} /></Button>
				<Button disabled><Checkmark size={24} /></Button>
			</div>
			<div class="col">
				<Button><Checkmark size={24} />Strong</Button>
				<Button hover><Checkmark size={24} />Strong hover</Button>
				<Button active><Checkmark size={24} />Strong active</Button>
				<Button focus><Checkmark size={24} />Strong focus</Button>
				<Button focus active><Checkmark size={24} />Strong focus active</Button>
				<Button disabled><Checkmark size={24} />Strong disabled</Button>
			</div>
			<div class="col">
				<Button>Strong<ArrowRight size={24} /></Button>
				<Button hover>Strong hover<ArrowRight size={24} /></Button>
				<Button active>Strong active<ArrowRight size={24} /></Button>
				<Button focus>Strong focus<ArrowRight size={24} /></Button>
				<Button focus active>Strong focus active<ArrowRight size={24} /></Button>
				<Button disabled>Strong disabled<ArrowRight size={24} /></Button>
			</div>
			<div class="col">
				<Button variant="secondary">Secondary</Button>
				<Button variant="secondary" hover>Secondary hover</Button>
				<Button variant="secondary" active>Secondary active</Button>
				<Button variant="secondary" focus>Secondary focus</Button>
				<Button variant="secondary" focus active>Secondary focus active</Button>
				<Button variant="secondary" disabled>Secondary disabled</Button>
			</div>
			<div class="col">
				<Button variant="ghost">Ghost</Button>
				<Button variant="ghost" hover>Ghost hover</Button>
				<Button variant="ghost" active>Ghost active</Button>
				<Button variant="ghost" focus>Ghost focus</Button>
				<Button variant="ghost" focus active>Ghost focus active</Button>
				<Button variant="ghost" disabled>Ghost disabled</Button>
			</div>
			<div class="col">
				<Button variant="solid">Solid</Button>
				<Button variant="solid" hover>Solid hover</Button>
				<Button variant="solid" active>Solid active</Button>
				<Button variant="solid" focus>Solid focus</Button>
				<Button variant="solid" focus active>Solid focus active</Button>
				<Button variant="solid" disabled>Solid disabled</Button>
			</div>
			<div class="col">
				<Button variant="darkoverlay">Dark overlay</Button>
				<Button variant="darkoverlay" hover>Dark overlay hover</Button>
				<Button variant="darkoverlay" active>Dark overlay active</Button>
				<Button variant="darkoverlay" focus>Dark overlay focus</Button>
				<Button variant="darkoverlay" focus active>Dark overlay focus active</Button>
				<Button variant="darkoverlay" disabled>Dark overlay disabled</Button>
			</div>
			<div class="col">
				<Button variant="lightoverlay">Light overlay</Button>
				<Button variant="lightoverlay" hover>Light overlay hover</Button>
				<Button variant="lightoverlay" active>Light overlay active</Button>
				<Button variant="lightoverlay" focus>Light overlay focus</Button>
				<Button variant="lightoverlay" focus active>Light overlay focus active</Button>
				<Button variant="lightoverlay" disabled>Light overlay disabled</Button>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<Button dimension="large">Strong</Button>
				<Button dimension="large" hover>Strong hover</Button>
				<Button dimension="large" active>Strong active</Button>
				<Button dimension="large" focus>Strong focus</Button>
				<Button dimension="large" focus active>Strong focus active</Button>
				<Button dimension="large" disabled>Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large"><Checkmark size={32} /></Button>
				<Button dimension="large" hover><Checkmark size={32} /></Button>
				<Button dimension="large" active><Checkmark size={32} /></Button>
				<Button dimension="large" focus><Checkmark size={32} /></Button>
				<Button dimension="large" focus active><Checkmark size={32} /></Button>
				<Button dimension="large" disabled><Checkmark size={32} /></Button>
			</div>
			<div class="col">
				<Button dimension="large"><Checkmark size={32} />Strong</Button>
				<Button dimension="large" hover><Checkmark size={32} />Strong hover</Button>
				<Button dimension="large" active><Checkmark size={32} />Strong active</Button>
				<Button dimension="large" focus><Checkmark size={32} />Strong focus</Button>
				<Button dimension="large" focus active><Checkmark size={32} />Strong focus active</Button>
				<Button dimension="large" disabled><Checkmark size={32} />Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large">Strong<ArrowRight size={32} /></Button>
				<Button dimension="large" hover>Strong hover<ArrowRight size={32} /></Button>
				<Button dimension="large" active>Strong active<ArrowRight size={32} /></Button>
				<Button dimension="large" focus>Strong focus<ArrowRight size={32} /></Button>
				<Button dimension="large" focus active>Strong focus active<ArrowRight size={32} /></Button>
				<Button dimension="large" disabled>Strong disabled<ArrowRight size={32} /></Button>
			</div>
			<div class="col">
				<Button dimension="large" variant="secondary">Secondary</Button>
				<Button dimension="large" variant="secondary" hover>Secondary hover</Button>
				<Button dimension="large" variant="secondary" active>Secondary active</Button>
				<Button dimension="large" variant="secondary" focus>Secondary focus</Button>
				<Button dimension="large" variant="secondary" focus active>Secondary focus active</Button>
				<Button dimension="large" variant="secondary" disabled>Secondary disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large" variant="ghost">Ghost</Button>
				<Button dimension="large" variant="ghost" hover>Ghost hover</Button>
				<Button dimension="large" variant="ghost" active>Ghost active</Button>
				<Button dimension="large" variant="ghost" focus>Ghost focus</Button>
				<Button dimension="large" variant="ghost" focus active>Ghost focus active</Button>
				<Button dimension="large" variant="ghost" disabled>Ghost disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large" variant="solid">Solid</Button>
				<Button dimension="large" variant="solid" hover>Solid hover</Button>
				<Button dimension="large" variant="solid" active>Solid active</Button>
				<Button dimension="large" variant="solid" focus>Solid focus</Button>
				<Button dimension="large" variant="solid" focus active>Solid focus active</Button>
				<Button dimension="large" variant="solid" disabled>Solid disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large" variant="darkoverlay">Dark overlay</Button>
				<Button dimension="large" variant="darkoverlay" hover>Dark overlay hover</Button>
				<Button dimension="large" variant="darkoverlay" active>Dark overlay active</Button>
				<Button dimension="large" variant="darkoverlay" focus>Dark overlay focus</Button>
				<Button dimension="large" variant="darkoverlay" focus active
					>Dark overlay focus active</Button
				>
				<Button dimension="large" variant="darkoverlay" disabled>Dark overlay disabled</Button>
			</div>
			<div class="col">
				<Button dimension="large" variant="lightoverlay">Light overlay</Button>
				<Button dimension="large" variant="lightoverlay" hover>Light overlay hover</Button>
				<Button dimension="large" variant="lightoverlay" active>Light overlay active</Button>
				<Button dimension="large" variant="lightoverlay" focus>Light overlay focus</Button>
				<Button dimension="large" variant="lightoverlay" focus active
					>Light overlay focus active</Button
				>
				<Button dimension="large" variant="lightoverlay" disabled>Light overlay disabled</Button>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<Button dimension="compact">Strong</Button>
				<Button dimension="compact" hover>Strong hover</Button>
				<Button dimension="compact" active>Strong active</Button>
				<Button dimension="compact" focus>Strong focus</Button>
				<Button dimension="compact" focus active>Strong focus active</Button>
				<Button dimension="compact" disabled>Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact"><Checkmark size={24} /></Button>
				<Button dimension="compact" hover><Checkmark size={24} /></Button>
				<Button dimension="compact" active><Checkmark size={24} /></Button>
				<Button dimension="compact" focus><Checkmark size={24} /></Button>
				<Button dimension="compact" focus active><Checkmark size={24} /></Button>
				<Button dimension="compact" disabled><Checkmark size={24} /></Button>
			</div>
			<div class="col">
				<Button dimension="compact"><Checkmark size={24} />Strong</Button>
				<Button dimension="compact" hover><Checkmark size={24} />Strong hover</Button>
				<Button dimension="compact" active><Checkmark size={24} />Strong active</Button>
				<Button dimension="compact" focus><Checkmark size={24} />Strong focus</Button>
				<Button dimension="compact" focus active><Checkmark size={24} />Strong focus active</Button>
				<Button dimension="compact" disabled><Checkmark size={24} />Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact">Strong<ArrowRight size={24} /></Button>
				<Button dimension="compact" hover>Strong hover<ArrowRight size={24} /></Button>
				<Button dimension="compact" active>Strong active<ArrowRight size={24} /></Button>
				<Button dimension="compact" focus>Strong focus<ArrowRight size={24} /></Button>
				<Button dimension="compact" focus active>Strong focus active<ArrowRight size={24} /></Button
				>
				<Button dimension="compact" disabled>Strong disabled<ArrowRight size={24} /></Button>
			</div>
			<div class="col">
				<Button dimension="compact" variant="secondary">Secondary</Button>
				<Button dimension="compact" variant="secondary" hover>Secondary hover</Button>
				<Button dimension="compact" variant="secondary" active>Secondary active</Button>
				<Button dimension="compact" variant="secondary" focus>Secondary focus</Button>
				<Button dimension="compact" variant="secondary" focus active>Secondary focus active</Button>
				<Button dimension="compact" variant="secondary" disabled>Secondary disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact" variant="ghost">Ghost</Button>
				<Button dimension="compact" variant="ghost" hover>Ghost hover</Button>
				<Button dimension="compact" variant="ghost" active>Ghost active</Button>
				<Button dimension="compact" variant="ghost" focus>Ghost focus</Button>
				<Button dimension="compact" variant="ghost" focus active>Ghost focus active</Button>
				<Button dimension="compact" variant="ghost" disabled>Ghost disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact" variant="solid">Solid</Button>
				<Button dimension="compact" variant="solid" hover>Solid hover</Button>
				<Button dimension="compact" variant="solid" active>Solid active</Button>
				<Button dimension="compact" variant="solid" focus>Solid focus</Button>
				<Button dimension="compact" variant="solid" focus active>Solid focus active</Button>
				<Button dimension="compact" variant="solid" disabled>Solid disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact" variant="darkoverlay">Dark overlay</Button>
				<Button dimension="compact" variant="darkoverlay" hover>Dark overlay hover</Button>
				<Button dimension="compact" variant="darkoverlay" active>Dark overlay active</Button>
				<Button dimension="compact" variant="darkoverlay" focus>Dark overlay focus</Button>
				<Button dimension="compact" variant="darkoverlay" focus active
					>Dark overlay focus active</Button
				>
				<Button dimension="compact" variant="darkoverlay" disabled>Dark overlay disabled</Button>
			</div>
			<div class="col">
				<Button dimension="compact" variant="lightoverlay">Light overlay</Button>
				<Button dimension="compact" variant="lightoverlay" hover>Light overlay hover</Button>
				<Button dimension="compact" variant="lightoverlay" active>Light overlay active</Button>
				<Button dimension="compact" variant="lightoverlay" focus>Light overlay focus</Button>
				<Button dimension="compact" variant="lightoverlay" focus active
					>Light overlay focus active</Button
				>
				<Button dimension="compact" variant="lightoverlay" disabled>Light overlay disabled</Button>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<Button dimension="small">Strong</Button>
				<Button dimension="small" hover>Strong hover</Button>
				<Button dimension="small" active>Strong active</Button>
				<Button dimension="small" focus>Strong focus</Button>
				<Button dimension="small" focus active>Strong focus active</Button>
				<Button dimension="small" disabled>Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small"><Checkmark size={16} /></Button>
				<Button dimension="small" hover><Checkmark size={16} /></Button>
				<Button dimension="small" active><Checkmark size={16} /></Button>
				<Button dimension="small" focus><Checkmark size={16} /></Button>
				<Button dimension="small" focus active><Checkmark size={16} /></Button>
				<Button dimension="small" disabled><Checkmark size={16} /></Button>
			</div>
			<div class="col">
				<Button dimension="small"><Checkmark size={16} />Strong</Button>
				<Button dimension="small" hover><Checkmark size={16} />Strong hover</Button>
				<Button dimension="small" active><Checkmark size={16} />Strong active</Button>
				<Button dimension="small" focus><Checkmark size={16} />Strong focus</Button>
				<Button dimension="small" focus active><Checkmark size={16} />Strong focus active</Button>
				<Button dimension="small" disabled><Checkmark size={16} />Strong disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small">Strong<ArrowRight size={16} /></Button>
				<Button dimension="small" hover>Strong hover<ArrowRight size={16} /></Button>
				<Button dimension="small" active>Strong active<ArrowRight size={16} /></Button>
				<Button dimension="small" focus>Strong focus<ArrowRight size={16} /></Button>
				<Button dimension="small" focus active>Strong focus active<ArrowRight size={16} /></Button>
				<Button dimension="small" disabled>Strong disabled<ArrowRight size={16} /></Button>
			</div>
			<div class="col">
				<Button dimension="small" variant="secondary">Secondary</Button>
				<Button dimension="small" variant="secondary" hover>Secondary hover</Button>
				<Button dimension="small" variant="secondary" active>Secondary active</Button>
				<Button dimension="small" variant="secondary" focus>Secondary focus</Button>
				<Button dimension="small" variant="secondary" focus active>Secondary focus active</Button>
				<Button dimension="small" variant="secondary" disabled>Secondary disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small" variant="ghost">Ghost</Button>
				<Button dimension="small" variant="ghost" hover>Ghost hover</Button>
				<Button dimension="small" variant="ghost" active>Ghost active</Button>
				<Button dimension="small" variant="ghost" focus>Ghost focus</Button>
				<Button dimension="small" variant="ghost" focus active>Ghost focus active</Button>
				<Button dimension="small" variant="ghost" disabled>Ghost disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small" variant="solid">Solid</Button>
				<Button dimension="small" variant="solid" hover>Solid hover</Button>
				<Button dimension="small" variant="solid" active>Solid active</Button>
				<Button dimension="small" variant="solid" focus>Solid focus</Button>
				<Button dimension="small" variant="solid" focus active>Solid focus active</Button>
				<Button dimension="small" variant="solid" disabled>Solid disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small" variant="darkoverlay">Dark overlay</Button>
				<Button dimension="small" variant="darkoverlay" hover>Dark overlay hover</Button>
				<Button dimension="small" variant="darkoverlay" active>Dark overlay active</Button>
				<Button dimension="small" variant="darkoverlay" focus>Dark overlay focus</Button>
				<Button dimension="small" variant="darkoverlay" focus active
					>Dark overlay focus active</Button
				>
				<Button dimension="small" variant="darkoverlay" disabled>Dark overlay disabled</Button>
			</div>
			<div class="col">
				<Button dimension="small" variant="lightoverlay">Light overlay</Button>
				<Button dimension="small" variant="lightoverlay" hover>Light overlay hover</Button>
				<Button dimension="small" variant="lightoverlay" active>Light overlay active</Button>
				<Button dimension="small" variant="lightoverlay" focus>Light overlay focus</Button>
				<Button dimension="small" variant="lightoverlay" focus active
					>Light overlay focus active</Button
				>
				<Button dimension="small" variant="lightoverlay" disabled>Light overlay disabled</Button>
			</div>
		</div>
	</section>
	<section id="checkbox">
		<Typography variant="h1">Checkbox</Typography>
		<div class="row">
			<div class="col">
				<Checkbox label="Unselected" />
				<Checkbox label="Hover unselected" hover />
				<Checkbox label="Pressed unselected" active />
				<Checkbox label="Focused unselected" focus />
				<Checkbox label="Disabled unselected" disabled />
				<Checkbox label="Selected" checked />
				<Checkbox label="Hover selected" checked hover />
				<Checkbox label="Pressed selected" checked active />
				<Checkbox label="Focused selected" checked focus />
				<Checkbox label="Disabled selected" checked disabled />
			</div>
			<div class="col">
				<Checkbox dimension="large" label="Unselected" />
				<Checkbox dimension="large" label="Hover unselected" hover />
				<Checkbox dimension="large" label="Pressed unselected" active />
				<Checkbox dimension="large" label="Focused unselected" focus />
				<Checkbox dimension="large" label="Disabled unselected" disabled />
				<Checkbox dimension="large" label="Selected" checked />
				<Checkbox dimension="large" label="Hover selected" checked hover />
				<Checkbox dimension="large" label="Pressed selected" checked active />
				<Checkbox dimension="large" label="Focused selected" checked focus />
				<Checkbox dimension="large" label="Disabled selected" checked disabled />
			</div>
			<div class="col">
				<Checkbox dimension="compact" label="Unselected" />
				<Checkbox dimension="compact" label="Hover unselected" hover />
				<Checkbox dimension="compact" label="Pressed unselected" active />
				<Checkbox dimension="compact" label="Focused unselected" focus />
				<Checkbox dimension="compact" label="Disabled unselected" disabled />
				<Checkbox dimension="compact" label="Selected" checked />
				<Checkbox dimension="compact" label="Hover selected" checked hover />
				<Checkbox dimension="compact" label="Pressed selected" checked active />
				<Checkbox dimension="compact" label="Focused selected" checked focus />
				<Checkbox dimension="compact" label="Disabled selected" checked disabled />
			</div>
			<div class="col">
				<Checkbox dimension="small" label="Unselected" />
				<Checkbox dimension="small" label="Hover unselected" hover />
				<Checkbox dimension="small" label="Pressed unselected" active />
				<Checkbox dimension="small" label="Focused unselected" focus />
				<Checkbox dimension="small" label="Disabled unselected" disabled />
				<Checkbox dimension="small" label="Selected" checked />
				<Checkbox dimension="small" label="Hover selected" checked hover />
				<Checkbox dimension="small" label="Pressed selected" checked active />
				<Checkbox dimension="small" label="Focused selected" checked focus />
				<Checkbox dimension="small" label="Disabled selected" checked disabled />
			</div>
		</div>
	</section>
	<section id="radio">
		<Typography variant="h1">Radio button</Typography>
		<div class="row">
			<div class="col">
				<RadioGroup>
					{#snippet helperText()}
						Helper text
					{/snippet}
					{#snippet label()}
						Default
					{/snippet}
					<Radio name="defaultD">Unselected</Radio>
					<Radio name="hoverD" hover>Hover unselected</Radio>
					<Radio name="activeD" active>Pressed unselected</Radio>
					<Radio name="focusD" focus>Focus unselected</Radio>
					<Radio name="disabledD" disabled>Focus unselected</Radio>
					<Radio name="defaultD" checked>Selected</Radio>
					<Radio name="hoverD" hover checked>Hover selected</Radio>
					<Radio name="activeD" active checked>Pressed selected</Radio>
					<Radio name="focusD" focus checked>Focus selected</Radio>
					<Radio name="disabledD" disabled checked>Disabled selected</Radio>
				</RadioGroup>
			</div>
			<div class="col">
				<RadioGroup dimension="large">
					{#snippet helperText()}
						Helper text
					{/snippet}
					{#snippet label()}
						Large
					{/snippet}
					<Radio name="defaultL">Unselected</Radio>
					<Radio name="hoverL" hover>Hover unselected</Radio>
					<Radio name="activeL" active>Pressed unselected</Radio>
					<Radio name="focusL" focus>Focus unselected</Radio>
					<Radio name="disabledL" disabled>Focus unselected</Radio>
					<Radio name="defaultL" checked>Selected</Radio>
					<Radio name="hoverL" hover checked>Hover selected</Radio>
					<Radio name="activeL" active checked>Pressed selected</Radio>
					<Radio name="focusL" focus checked>Focus selected</Radio>
					<Radio name="disabledL" disabled checked>Disabled selected</Radio>
				</RadioGroup>
			</div>
			<div class="col">
				<RadioGroup dimension="compact">
					{#snippet helperText()}
						Helper text
					{/snippet}
					{#snippet label()}
						Compact
					{/snippet}
					<Radio name="defaultC">Unselected</Radio>
					<Radio name="hoverC" hover>Hover unselected</Radio>
					<Radio name="activeC" active>Pressed unselected</Radio>
					<Radio name="focusC" focus>Focus unselected</Radio>
					<Radio name="disabledC" disabled>Focus unselected</Radio>
					<Radio name="defaultC" checked>Selected</Radio>
					<Radio name="hoverC" hover checked>Hover selected</Radio>
					<Radio name="activeC" active checked>Pressed selected</Radio>
					<Radio name="focusC" focus checked>Focus selected</Radio>
					<Radio name="disabledC" disabled checked>Disabled selected</Radio>
				</RadioGroup>
			</div>
			<div class="col">
				<RadioGroup dimension="small">
					{#snippet helperText()}
						Helper text
					{/snippet}
					{#snippet label()}
						Small
					{/snippet}
					<Radio name="defaultS">Unselected</Radio>
					<Radio name="hoverS" hover>Hover unselected</Radio>
					<Radio name="activeS" active>Pressed unselected</Radio>
					<Radio name="focusS" focus>Focus unselected</Radio>
					<Radio name="disabledS" disabled>Focus unselected</Radio>
					<Radio name="defaultS" checked>Selected</Radio>
					<Radio name="hoverS" hover checked>Hover selected</Radio>
					<Radio name="activeS" active checked>Pressed selected</Radio>
					<Radio name="focusS" focus checked>Focus selected</Radio>
					<Radio name="disabledS" disabled checked>Disabled selected</Radio>
				</RadioGroup>
			</div>
		</div>
	</section>
	<section id="switch">
		<Typography variant="h1">Switch</Typography>
		<div class="row">
			<div class="col">
				<Switch label="Off" />
				<Switch label="Hover off" hover />
				<Switch label="Active off" active />
				<Switch label="Focus off" focus />
				<Switch label="Disabled off" disabled />
				<Switch label="On" checked />
				<Switch label="Hover on" checked hover />
				<Switch label="Active on" checked active />
				<Switch label="Focus on" checked focus />
				<Switch label="Disabled on" checked disabled />
			</div>
			<div class="col">
				<Switch dimension="large" label="Off" />
				<Switch dimension="large" label="Hover off" hover />
				<Switch dimension="large" label="Active off" active />
				<Switch dimension="large" label="Focus off" focus />
				<Switch dimension="large" label="Disabled off" disabled />
				<Switch dimension="large" label="On" checked />
				<Switch dimension="large" label="Hover on" checked hover />
				<Switch dimension="large" label="Active on" checked active />
				<Switch dimension="large" label="Focus on" checked focus />
				<Switch dimension="large" label="Disabled on" checked disabled />
			</div>
			<div class="col">
				<Switch dimension="compact" label="Off" />
				<Switch dimension="compact" label="Hover off" hover />
				<Switch dimension="compact" label="Active off" active />
				<Switch dimension="compact" label="Focus off" focus />
				<Switch dimension="compact" label="Disabled off" disabled />
				<Switch dimension="compact" label="On" checked />
				<Switch dimension="compact" label="Hover on" checked hover />
				<Switch dimension="compact" label="Active on" checked active />
				<Switch dimension="compact" label="Focus on" checked focus />
				<Switch dimension="compact" label="Disabled on" checked disabled />
			</div>
			<div class="col">
				<Switch dimension="small" label="Off" />
				<Switch dimension="small" label="Hover off" hover />
				<Switch dimension="small" label="Active off" active />
				<Switch dimension="small" label="Focus off" focus />
				<Switch dimension="small" label="Disabled off" disabled />
				<Switch dimension="small" label="On" checked />
				<Switch dimension="small" label="Hover on" checked hover />
				<Switch dimension="small" label="Active on" checked active />
				<Switch dimension="small" label="Focus on" checked focus />
				<Switch dimension="small" label="Disabled on" checked disabled />
			</div>
		</div>
	</section>
	<section id="typography">
		<Typography variant="h1">Typography</Typography>
		<div class="row">
			<div class="col">
				<Typography variant="h1">h1 Title</Typography>
				<Typography variant="h2">h2 Title</Typography>
				<Typography variant="h3">h3 Title</Typography>
				<Typography variant="h4">h4 Title</Typography>
				<Typography variant="h5">h5 Title</Typography>
				<Typography variant="h6">h6 Title</Typography>
			</div>
			<div class="col">
				<Typography variant="large" element="p">Large paragraph</Typography>
				<Typography variant="default" element="p">Paragraph</Typography>
				<Typography variant="small" element="p">Small-paragraph</Typography>
			</div>
			<div class="col">
				<Typography>Sans</Typography>
				<Typography italic>Sans Italic</Typography>
				<Typography bold>Sans Bold</Typography>
				<Typography bold italic>Sans Bold Italic</Typography>
				<Typography font="serif">Serif</Typography>
				<Typography font="serif" italic>Serif Italic</Typography>
				<Typography font="serif" bold>Serif Bold</Typography>
				<Typography font="serif" bold italic>Serif Bold Italic</Typography>
				<Typography font="mono">Mono</Typography>
				<Typography font="mono" italic>Mono Italic</Typography>
				<Typography font="mono" bold>Mono Bold</Typography>
				<Typography font="mono" bold italic>Mono Bold Italic</Typography>
			</div>
		</div>
	</section>
	{#snippet error()}
		This is an error message
	{/snippet}
	<section>
		<Typography variant="h1">Input outline (vertical)</Typography>
		<div class="row">
			<div class="col">
				<Input label="Input label" placeholder="Placeholder">This is an optional helper text</Input>
				<Input label="Input label" value="With text">This is an optional helper text</Input>
				<Input label="Input label" value="Hover" hover>This is an optional helper text</Input>
				<Input label="Input label" value="Pressed" active>This is an optional helper text</Input>
				<Input label="Input label" value="Focused" focus>This is an optional helper text</Input>
				<Input label="Input label" value="Disabled" disabled>This is an optional helper text</Input>
				<Input label="Input label" value="With error" {error}>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="large" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input dimension="large" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="compact" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input dimension="compact" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="small" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input dimension="small" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
		</div>
		<Typography variant="h1">Input solid (vertical)</Typography>
		<div class="row">
			<div class="col">
				<Input variant="solid" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input variant="solid" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input variant="solid" dimension="large" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="large" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input variant="solid" dimension="compact" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="compact" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input variant="solid" dimension="small" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input variant="solid" dimension="small" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Input (horizontal)</Typography>
		<div class="row">
			<div class="col">
				<Input layout="horizontal" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input layout="horizontal" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="large" layout="horizontal" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input dimension="large" layout="horizontal" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="compact" layout="horizontal" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="compact" layout="horizontal" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="compact" layout="horizontal" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="compact" layout="horizontal" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="compact" layout="horizontal" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="compact" layout="horizontal" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input
					dimension="compact"
					layout="horizontal"
					label="Input label"
					value="With error"
					{error}>This is an optional helper text</Input
				>
			</div>
			<div class="col">
				<Input dimension="small" layout="horizontal" label="Input label" placeholder="Placeholder"
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="With text"
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="Hover" hover
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="Pressed" active
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="Focused" focus
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="Disabled" disabled
					>This is an optional helper text</Input
				>
				<Input dimension="small" layout="horizontal" label="Input label" value="With error" {error}
					>This is an optional helper text</Input
				>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Search input</Typography>
		<div class="row">
			<div class="col">
				<SearchInput placeholder="Placeholder" />
				<SearchInput value="" />
				<SearchInput value="Diete" />
				<SearchInput disabled />
			</div>
			<div class="col">
				<SearchInput dimension="large" placeholder="Placeholder" />
				<SearchInput dimension="large" value="" />
				<SearchInput dimension="large" value="Diete" />
				<SearchInput dimension="large" disabled />
			</div>
			<div class="col">
				<SearchInput dimension="compact" placeholder="Placeholder" />
				<SearchInput dimension="compact" value="" />
				<SearchInput dimension="compact" value="Diete" />
				<SearchInput dimension="compact" disabled />
			</div>
			<div class="col">
				<SearchInput dimension="small" placeholder="Placeholder" />
				<SearchInput dimension="small" value="" />
				<SearchInput dimension="small" value="Diete" />
				<SearchInput dimension="small" disabled />
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Search input (with button)</Typography>
		<div class="row">
			<div class="col">
				<SearchInput placeholder="Placeholder" withButton />
				<SearchInput value="" withButton />
				<SearchInput value="Diete" withButton />
				<SearchInput disabled withButton />
			</div>
			<div class="col">
				<SearchInput dimension="large" placeholder="Placeholder" withButton />
				<SearchInput dimension="large" value="" withButton />
				<SearchInput dimension="large" value="Diete" withButton />
				<SearchInput dimension="large" disabled withButton />
			</div>
			<div class="col">
				<SearchInput dimension="compact" placeholder="Placeholder" withButton />
				<SearchInput dimension="compact" value="" withButton />
				<SearchInput dimension="compact" value="Diete" withButton />
				<SearchInput dimension="compact" disabled withButton />
			</div>
			<div class="col">
				<SearchInput dimension="small" placeholder="Placeholder" withButton />
				<SearchInput dimension="small" value="" withButton />
				<SearchInput dimension="small" value="Diete" withButton />
				<SearchInput dimension="small" disabled withButton />
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Number input (vertical)</Typography>
		<div class="row">
			<div class="col">
				<NumberInput label="Number input" unit="EUR" placeholder="0"
					>This is an optional helper text</NumberInput
				>
				<NumberInput label="Number input" unit="EUR" placeholder="0" value="1420"
					>This is an optional helper text</NumberInput
				>
				<NumberInput label="Number input" unit="EUR" placeholder="0" value="1420" hover
					>This is an optional helper text</NumberInput
				>
				<NumberInput label="Number input" unit="EUR" placeholder="0" value="1420" active
					>This is an optional helper text</NumberInput
				>
				<NumberInput label="Number input" unit="EUR" placeholder="0" value="1420" focus
					>This is an optional helper text</NumberInput
				>
				<NumberInput label="Number input" unit="EUR" placeholder="0" value="1420" disabled
					>This is an optional helper text</NumberInput
				>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Number input (horizontal)</Typography>
		<div class="row">
			<div class="col">
				<NumberInput layout="horizontal" label="Number input" unit="EUR" placeholder="0"
					>This is an optional helper text</NumberInput
				>
				<NumberInput
					layout="horizontal"
					label="Number input"
					unit="EUR"
					placeholder="0"
					value="1420">This is an optional helper text</NumberInput
				>
				<NumberInput
					layout="horizontal"
					label="Number input"
					unit="EUR"
					placeholder="0"
					value="1420"
					hover>This is an optional helper text</NumberInput
				>
				<NumberInput
					layout="horizontal"
					label="Number input"
					unit="EUR"
					placeholder="0"
					value="1420"
					active>This is an optional helper text</NumberInput
				>
				<NumberInput
					layout="horizontal"
					label="Number input"
					unit="EUR"
					placeholder="0"
					value="1420"
					focus>This is an optional helper text</NumberInput
				>
				<NumberInput
					layout="horizontal"
					label="Number input"
					unit="EUR"
					placeholder="0"
					value="1420"
					disabled>This is an optional helper text</NumberInput
				>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Date input</Typography>
		<div class="row">
			<div class="col">
				<DateInput label="Date picker" />
				<DateInput label="Date picker" value="2024-05-01" />
				<DateInput label="Date picker" value="2024-05-01" hover />
				<DateInput label="Date picker" value="2024-05-01" active />
				<DateInput label="Date picker" value="2024-05-01" focus />
				<DateInput label="Date picker" value="2024-05-01" disabled />
			</div>
			<div class="col">
				<DateInput dimension="large" label="Date picker" />
				<DateInput dimension="large" label="Date picker" value="2024-05-01" />
				<DateInput dimension="large" label="Date picker" value="2024-05-01" hover />
				<DateInput dimension="large" label="Date picker" value="2024-05-01" active />
				<DateInput dimension="large" label="Date picker" value="2024-05-01" focus />
				<DateInput dimension="large" label="Date picker" value="2024-05-01" disabled />
			</div>
			<div class="col">
				<DateInput dimension="compact" label="Date picker" />
				<DateInput dimension="compact" label="Date picker" value="2024-05-01" />
				<DateInput dimension="compact" label="Date picker" value="2024-05-01" hover />
				<DateInput dimension="compact" label="Date picker" value="2024-05-01" active />
				<DateInput dimension="compact" label="Date picker" value="2024-05-01" focus />
				<DateInput dimension="compact" label="Date picker" value="2024-05-01" disabled />
			</div>
			<div class="col">
				<DateInput dimension="small" label="Date picker" />
				<DateInput dimension="small" label="Date picker" value="2024-05-01" />
				<DateInput dimension="small" label="Date picker" value="2024-05-01" hover />
				<DateInput dimension="small" label="Date picker" value="2024-05-01" active />
				<DateInput dimension="small" label="Date picker" value="2024-05-01" focus />
				<DateInput dimension="small" label="Date picker" value="2024-05-01" disabled />
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Textarea (outline)</Typography>
		{#snippet helperText()}
			This is an optional helper text
		{/snippet}
		<div class="row">
			<div class="col">
				<Textarea label="Input label" {helperText} placeholder="Placeholder"></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					hover
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					active
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					focus
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea dimension="large" label="Input label" {helperText} placeholder="Placeholder"
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					hover
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					active
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					focus
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea dimension="compact" label="Input label" {helperText} placeholder="Placeholder"
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					hover
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					active
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					focus
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea dimension="small" label="Input label" {helperText} placeholder="Placeholder"
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					hover
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					active
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					focus
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					disabled
				></Textarea>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Textarea (solid)</Typography>
		{#snippet helperText()}
			This is an optional helper text
		{/snippet}
		<div class="row">
			<div class="col">
				<Textarea label="Input label" {helperText} placeholder="Placeholder" variant="solid"
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					hover
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					active
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					focus
				></Textarea>
				<Textarea
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					variant="solid"
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					hover
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					active
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					focus
				></Textarea>
				<Textarea
					dimension="large"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					variant="solid"
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					hover
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					active
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					focus
				></Textarea>
				<Textarea
					dimension="compact"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					disabled
				></Textarea>
			</div>
			<div class="col">
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					variant="solid"
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					hover
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					active
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					focus
				></Textarea>
				<Textarea
					dimension="small"
					label="Input label"
					{helperText}
					placeholder="Placeholder"
					value="I'm baby glossier artisan cred austin, yuccie venmo aesthetic seitan franzen pour-over taiyaki."
					variant="solid"
					disabled
				></Textarea>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Select (outline)</Typography>
		<div class="row">
			<div class="col">
				<Select label="Outline select" placeholder="Placeholder" />
				<Select label="Outline select" placeholder="Placeholder" value="With value" />
				<Select label="Outline select" placeholder="Hover" hover />
				<Select label="Outline select" placeholder="Active" hover />
				<Select label="Outline select" placeholder="Active" focus />
				<Select label="Outline select" value="Disabled" disabled />
			</div>
			<div class="col">
				<Select dimension="large" label="Outline select" placeholder="Placeholder" />
				<Select
					dimension="large"
					label="Outline select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select dimension="large" label="Outline select" placeholder="Hover" hover />
				<Select dimension="large" label="Outline select" placeholder="Active" hover />
				<Select dimension="large" label="Outline select" placeholder="Active" focus />
				<Select dimension="large" label="Outline select" value="Disabled" disabled />
			</div>
			<div class="col">
				<Select dimension="compact" label="Outline select" placeholder="Placeholder" />
				<Select
					dimension="compact"
					label="Outline select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select dimension="compact" label="Outline select" placeholder="Hover" hover />
				<Select dimension="compact" label="Outline select" placeholder="Active" hover />
				<Select dimension="compact" label="Outline select" placeholder="Active" focus />
				<Select dimension="compact" label="Outline select" value="Disabled" disabled />
			</div>
			<div class="col">
				<Select dimension="small" label="Outline select" placeholder="Placeholder" />
				<Select
					dimension="small"
					label="Outline select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select dimension="small" label="Outline select" placeholder="Hover" hover />
				<Select dimension="small" label="Outline select" placeholder="Active" hover />
				<Select dimension="small" label="Outline select" placeholder="Active" focus />
				<Select dimension="small" label="Outline select" value="Disabled" disabled />
			</div>
		</div>
		<Typography variant="h1">Select (solid)</Typography>
		<div class="row">
			<div class="col">
				<Select variant="solid" label="Solid select" placeholder="Placeholder" />
				<Select variant="solid" label="Solid select" placeholder="Placeholder" value="With value" />
				<Select variant="solid" label="Solid select" placeholder="Hover" hover />
				<Select variant="solid" label="Solid select" placeholder="Active" hover />
				<Select variant="solid" label="Solid select" placeholder="Active" focus />
				<Select variant="solid" label="Solid select" value="Disabled" disabled />
			</div>
			<div class="col">
				<Select variant="solid" dimension="large" label="Solid select" placeholder="Placeholder" />
				<Select
					variant="solid"
					dimension="large"
					label="Solid select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select variant="solid" dimension="large" label="Solid select" placeholder="Hover" hover />
				<Select variant="solid" dimension="large" label="Solid select" placeholder="Active" hover />
				<Select variant="solid" dimension="large" label="Solid select" placeholder="Active" focus />
				<Select variant="solid" dimension="large" label="Solid select" value="Disabled" disabled />
			</div>
			<div class="col">
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					placeholder="Placeholder"
				/>
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					placeholder="Hover"
					hover
				/>
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					placeholder="Active"
					hover
				/>
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					placeholder="Active"
					focus
				/>
				<Select
					variant="solid"
					dimension="compact"
					label="Solid select"
					value="Disabled"
					disabled
				/>
			</div>
			<div class="col">
				<Select variant="solid" dimension="small" label="Solid select" placeholder="Placeholder" />
				<Select
					variant="solid"
					dimension="small"
					label="Solid select"
					placeholder="Placeholder"
					value="With value"
				/>
				<Select variant="solid" dimension="small" label="Solid select" placeholder="Hover" hover />
				<Select variant="solid" dimension="small" label="Solid select" placeholder="Active" hover />
				<Select variant="solid" dimension="small" label="Solid select" placeholder="Active" focus />
				<Select variant="solid" dimension="small" label="Solid select" value="Disabled" disabled />
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Select</Typography>
		<div class="row">
			<div class="col">
				<Select label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						Without any default value.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						With default value.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" label="Select label" placeholder="Placeholder" hover>
					{#snippet helperText()}
						Hover.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" label="Select label" placeholder="Placeholder" active>
					{#snippet helperText()}
						Pressed.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" label="Select label" placeholder="Placeholder" focus>
					{#snippet helperText()}
						Focus.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" label="Select label" placeholder="Placeholder" disabled>
					{#snippet helperText()}
						Disabled.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select dimension="large" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" dimension="large" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select dimension="compact" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" dimension="compact" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select dimension="small" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select value="2" dimension="small" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
		</div>
	</section>
	<section>
		<Typography variant="h1">Select (horizontal)</Typography>
		<div class="row">
			<div class="col">
				<Select layout="horizontal" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						Without any default value.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select layout="horizontal" value="2" label="Select label" placeholder="Placeholder">
					{#snippet helperText()}
						With default value.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select layout="horizontal" value="2" label="Select label" placeholder="Placeholder" hover>
					{#snippet helperText()}
						Hover.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select layout="horizontal" value="2" label="Select label" placeholder="Placeholder" active>
					{#snippet helperText()}
						Pressed.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select layout="horizontal" value="2" label="Select label" placeholder="Placeholder" focus>
					{#snippet helperText()}
						Focus.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select
					layout="horizontal"
					value="2"
					label="Select label"
					placeholder="Placeholder"
					disabled
				>
					{#snippet helperText()}
						Disabled.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select
					layout="horizontal"
					dimension="large"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select
					layout="horizontal"
					value="2"
					dimension="large"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select
					layout="horizontal"
					dimension="compact"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select
					layout="horizontal"
					value="2"
					dimension="compact"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
			<div class="col">
				<Select
					layout="horizontal"
					dimension="small"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
				<Select
					layout="horizontal"
					value="2"
					dimension="small"
					label="Select label"
					placeholder="Placeholder"
				>
					{#snippet helperText()}
						This is some helper text.
					{/snippet}
					<Option value="1">Label 1</Option>
					<Option value="2">Label 2</Option>
					<Option value="3">Label 3</Option>
					<Option value="4">Label 4</Option>
					<Option value="5">Label 5</Option>
					<Option value="6">Label 6</Option>
					<Option value="7">Label 7</Option>
				</Select>
			</div>
		</div>
	</section>
	<section id="menu">
		<Typography variant="h1">Menu</Typography>
		{#snippet content()}
			Organic taiyaki
		{/snippet}
		<div class="row">
			<div class="col">
				<MenuTitle bold>
					{#snippet content()}
						List title
					{/snippet}
				</MenuTitle>
				<MenuTitle bold hover>
					{#snippet content()}
						List title hover
					{/snippet}
				</MenuTitle>
				<MenuTitle bold active>
					{#snippet content()}
						List title pressed
					{/snippet}
				</MenuTitle>
				<MenuTitle bold focus>
					{#snippet content()}
						List title focus
					{/snippet}
				</MenuTitle>
				<MenuTitle bold disabled>
					{#snippet content()}
						List title disabled
					{/snippet}
				</MenuTitle>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<MenuTitle bold>
					{#snippet content()}
						Closed
					{/snippet}
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle bold open>
					{#snippet content()}
						Opened
					{/snippet}
					<MenuItem href="#button" disabled>Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle bold disabled>
					{#snippet content()}
						Disabled
					{/snippet}
				</MenuTitle>
				<MenuTitle bold open disabled>
					{#snippet content()}
						Open disabled
					{/snippet}
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
			</div>
			<div class="col">
				<MenuTitle bold {content} dimension="large">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle bold {content} dimension="large" open />
			</div>
			<div class="col">
				<MenuTitle bold {content} dimension="compact">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle bold {content} dimension="compact" open />
			</div>
			<div class="col">
				<MenuTitle bold {content} dimension="small">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle bold {content} dimension="small" open />
			</div>
		</div>
		<div class="row">
			<div class="col">
				<MenuTitle {content}>
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle {content} open />
			</div>
			<div class="col">
				<MenuTitle {content} dimension="large">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle {content} dimension="large" open />
			</div>
			<div class="col">
				<MenuTitle {content} dimension="compact">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle {content} dimension="compact" open />
			</div>
			<div class="col">
				<MenuTitle {content} dimension="small">
					<MenuItem href="#button">Button</MenuItem>
					<MenuItem href="#checkbox">Checkbox</MenuItem>
					<MenuItem href="#radio">Radio button</MenuItem>
					<MenuItem href="#switch">Switch</MenuItem>
					<MenuItem href="#typography">Typography</MenuItem>
				</MenuTitle>
				<MenuTitle {content} dimension="small" open />
			</div>
		</div>
	</section>
	<section>
		{#snippet helperText()}
			This is an optional helper text
		{/snippet}
		<Typography variant="h1">Slider</Typography>
		<div class="row">
			<div class="col">
				<Slider min={0} max={100} value={50} step={10} {helperText} showSteps>With step</Slider>
				<Slider min={0} max={100} value={50} step={10} {helperText} hover showSteps
					>Slider label</Slider
				>
				<Slider min={0} max={100} value={50} step={10} {helperText} active showSteps
					>Slider label</Slider
				>
				<Slider min={0} max={100} value={50} step={10} {helperText} focus showSteps
					>Slider label</Slider
				>
				<Slider min={0} max={100} value={50} step={10} {helperText} focus active showSteps
					>Slider label</Slider
				>
				<Slider min={0} max={100} value={50} step={10} {helperText} disabled>Slider label</Slider>
			</div>
			<div class="col">
				<Slider dimension="large" min={0} max={100} value={50} step={10} {helperText} showSteps
					>With step</Slider
				>
				<Slider
					dimension="large"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					hover
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					disabled
					showSteps>Slider label</Slider
				>
			</div>
			<div class="col">
				<Slider dimension="compact" min={0} max={100} value={50} step={10} {helperText} showSteps
					>With step</Slider
				>
				<Slider
					dimension="compact"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					hover
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					disabled
					showSteps>Slider label</Slider
				>
			</div>
			<div class="col">
				<Slider dimension="small" min={0} max={100} value={50} step={10} {helperText} showSteps
					>With step</Slider
				>
				<Slider
					dimension="small"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					hover
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					focus
					active
					showSteps>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={0}
					max={100}
					value={50}
					step={10}
					{helperText}
					disabled
					showSteps>Slider label</Slider
				>
			</div>
		</div>
		<div class="row">
			<div class="col">
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered>Slider label</Slider>
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered hover
					>Slider label</Slider
				>
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered active
					>Slider label</Slider
				>
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered focus
					>Slider label</Slider
				>
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered focus active
					>Slider label</Slider
				>
				<Slider min={-5} max={5} value={-3} step={1} {helperText} centered disabled
					>Slider label</Slider
				>
			</div>
			<div class="col">
				<Slider dimension="large" min={-5} max={5} value={-3} step={1} {helperText} centered
					>Slider label</Slider
				>
				<Slider dimension="large" min={-5} max={5} value={-3} step={1} {helperText} centered hover
					>Slider label</Slider
				>
				<Slider dimension="large" min={-5} max={5} value={-3} step={1} {helperText} centered active
					>Slider label</Slider
				>
				<Slider dimension="large" min={-5} max={5} value={-3} step={1} {helperText} centered focus
					>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					focus
					active>Slider label</Slider
				>
				<Slider
					dimension="large"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					disabled>Slider label</Slider
				>
			</div>
			<div class="col">
				<Slider dimension="compact" min={-5} max={5} value={-3} step={1} {helperText} centered
					>Slider label</Slider
				>
				<Slider dimension="compact" min={-5} max={5} value={-3} step={1} {helperText} centered hover
					>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					active>Slider label</Slider
				>
				<Slider dimension="compact" min={-5} max={5} value={-3} step={1} {helperText} centered focus
					>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					focus
					active>Slider label</Slider
				>
				<Slider
					dimension="compact"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					disabled>Slider label</Slider
				>
			</div>
			<div class="col">
				<Slider dimension="small" min={-5} max={5} value={-3} step={1} {helperText} centered
					>Slider label</Slider
				>
				<Slider dimension="small" min={-5} max={5} value={-3} step={1} {helperText} centered hover
					>Slider label</Slider
				>
				<Slider dimension="small" min={-5} max={5} value={-3} step={1} {helperText} centered active
					>Slider label</Slider
				>
				<Slider dimension="small" min={-5} max={5} value={-3} step={1} {helperText} centered focus
					>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					focus
					active>Slider label</Slider
				>
				<Slider
					dimension="small"
					min={-5}
					max={5}
					value={-3}
					step={1}
					{helperText}
					centered
					disabled>Slider label</Slider
				>
			</div>
		</div>
		<div class="row">
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText}
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} hover
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} leftActive
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} rightActive
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} leftFocus
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} leftFocus leftActive
				>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} rightFocus
				>Slider label</RangeSlider
			>
			<RangeSlider
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider step={10} showSteps valueMin={0} valueMax={50} {helperText} disabled
				>Slider label</RangeSlider
			>
		</div>
		<div class="row">
			<RangeSlider dimension="large" step={10} showSteps valueMin={0} valueMax={50} {helperText}
				>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				hover>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="large"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				disabled>Slider label</RangeSlider
			>
		</div>
		<div class="row">
			<RangeSlider dimension="default" step={10} showSteps valueMin={0} valueMax={50} {helperText}
				>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				hover>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="default"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				disabled>Slider label</RangeSlider
			>
		</div>
		<div class="row">
			<RangeSlider dimension="small" step={10} showSteps valueMin={0} valueMax={50} {helperText}
				>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				hover>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				leftFocus
				leftActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				rightFocus
				rightActive>Slider label</RangeSlider
			>
			<RangeSlider
				dimension="small"
				step={10}
				showSteps
				valueMin={0}
				valueMax={50}
				{helperText}
				disabled>Slider label</RangeSlider
			>
		</div>
	</section>
	<section>
		<div class="row">
			<div class="col">
				<Badge>
					<CheckmarkFilled size={16} />
					Small badge
				</Badge>
				<Badge variant="strong">
					<CheckmarkFilled size={16} />
					Small badge
				</Badge>
				<Badge variant="dark-overlay">
					<CheckmarkFilled size={16} />
					Small badge
				</Badge>
				<Badge variant="light-overlay">
					<CheckmarkFilled size={16} />
					Small badge
				</Badge>
			</div>
			<div class="col">
				<div class="badge-row">
					<Typography variant="h5">h5 Title</Typography><Badge>Small badge</Badge>
				</div>
				<div class="badge-row">
					<NotificationNew size={16} />
					<Typography variant="h5">Messages</Typography>
					<Badge variant="strong">16</Badge>
				</div>
				<div class="badge-row">
					<Typography variant="h5">Aqualung divide</Typography>
					<Badge variant="strong">NEW</Badge>
				</div>
				<div class="badge-row">
					<Badge variant="light-overlay">
						<ThumbsUpFilled size={16} />
						21
					</Badge>
					<Badge variant="light-overlay">
						<ThumbsDown size={16} />
						6
					</Badge>
				</div>
			</div>
			<div class="col">
				<Badge dimension="large">
					<Error size={24} />
					Large badge
				</Badge>
				<Badge dimension="large" variant="strong">
					<Error size={24} />
					Large badge
				</Badge>
				<Badge dimension="large" variant="dark-overlay">
					<Error size={24} />
					Large badge
				</Badge>
				<Badge dimension="large" variant="light-overlay">
					<Error size={24} />
					Large badge
				</Badge>
			</div>
			<div class="col">
				<div class="badge-row">
					<Typography variant="h4">h4 Title</Typography><Badge dimension="large">Large badge</Badge>
				</div>
				<div class="badge-row">
					<Typography variant="h4">h4 Title</Typography><Badge dimension="small">Small badge</Badge>
				</div>
				<div class="badge-row">
					<Typography variant="h4">System</Typography>
					<Badge variant="default">
						<CheckmarkFilled size={16} />
						Updated
					</Badge>
				</div>
				<div class="badge-row">
					<Typography variant="h3">David's computer</Typography>
					<Badge dimension="large" variant="strong">
						<Error size={24} />
						Error
					</Badge>
				</div>
				<div class="badge-row">
					<Typography variant="h4">Posts</Typography>
					<Badge dimension="large" variant="light-overlay">12</Badge>
				</div>
			</div>
		</div>
	</section>
	<section>
		<div class="row">
			<div class="col">
				<Button><Loader color="low" /></Button>
				<Loader dimension="large" />
			</div>
		</div>
	</section>
	<section>
		<div class="row">
			<ProgressBar value={50}>Loading...</ProgressBar>
		</div>
		<div class="row">
			<ProgressBar dimension="large" value={50}>Loading...</ProgressBar>
		</div>
		<div class="row">
			<ProgressBar dimension="small" value={50}>Loading...</ProgressBar>
		</div>
	</section>
	<section>
		<div class="row">
			<div class="col">
				<NumberInput label="Number input" placeholder="Add number" />
				<SearchInput label="Search input" placeholder="Add text" />
				<ColorInput label="Color input" placeholder="Add color" />
				<DateInput label="Date input" />
			</div>
		</div>
	</section>
	<section class="table">
		<Table>
			<Thead>
				<Tr>
					<Th noPadding
						><Checkbox
							class="align"
							label="Table header"
							mixed={selectedCount > 0 && selectedCount < selected.length}
							bind:checked={selectionAll}
							onclick={selectAll}
						/><ChevronDown class="align" size={24} /></Th
					>
					<Th>Table header</Th>
					<Th>Table header</Th>
					<Th>Table header</Th>
					<Th>Table header</Th>
				</Tr>
			</Thead>
			<Tbody>
				<Tr class="with-checkbox" active={selected[0]}>
					<Td noPadding
						><Checkbox
							class="align"
							label="Cornhole"
							bind:checked={selected[0]}
							onclick={() => toggleSelection(0)}
						/></Td
					>
					<Td>Glossier</Td>
					<Td>Skateboard</Td>
					<Td>Paleo</Td>
					<Td>Fingerstache</Td>
				</Tr>
				<Tr class="with-checkbox" active={selected[1]}>
					<Td noPadding
						><Checkbox
							class="align"
							label="Cornhole"
							bind:checked={selected[1]}
							onclick={() => toggleSelection(1)}
						/></Td
					>
					<Td>Glossier</Td>
					<Td>Skateboard</Td>
					<Td>Paleo</Td>
					<Td>Fingerstache</Td>
				</Tr>
				<Tr class="with-checkbox" active={selected[2]}>
					<Td noPadding
						><Checkbox
							class="align"
							label="Cornhole"
							bind:checked={selected[2]}
							onclick={() => toggleSelection(2)}
						/></Td
					>
					<Td>Glossier</Td>
					<Td>Skateboard</Td>
					<Td>Paleo</Td>
					<Td>Fingerstache</Td>
				</Tr>
			</Tbody>
		</Table>
	</section>
	<section class="table">
		<Table>
			<Tr>
				<Th><div class="space-between">Table header<ChevronDown class="align" size={24} /></div></Th
				>
				<Th>Simple text</Th>
				<Th>Longer text</Th>
				<Th>Badge</Th>
				<Th style="text-align: right;">Number</Th>
				<Th style="text-align: right;">Button</Th>
			</Tr>
			<Tr>
				<Td>Cornhole</Td>
				<Td>Glossier</Td>
				<Td>Copper mug skateboard fingerstache</Td>
				<Td><Badge dimension="small"><CheckmarkFilled size={16} />Small Badge</Badge></Td>
				<Td style="text-align: right;">999 EUR</Td>
				<Td style="text-align: right;"
					><Button variant="secondary" dimension="compact">Outline button</Button></Td
				>
			</Tr>
			<Tr>
				<Td>Cornhole</Td>
				<Td>Glossier</Td>
				<Td>Copper mug skateboard fingerstache</Td>
				<Td><Badge dimension="small"><CheckmarkFilled size={16} />Small Badge</Badge></Td>
				<Td style="text-align: right;">999 EUR</Td>
				<Td style="text-align: right;"
					><Button variant="secondary" dimension="compact">Outline button</Button></Td
				>
			</Tr>
		</Table>
	</section>
</div>

<style>
	.table {
		margin-bottom: 5rem;
	}
	:global(.align) {
		vertical-align: middle;
	}
	.space-between {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}
	.page-wrapper {
		background-color: var(--colors-ultra-low);
	}
	.row {
		display: flex;
		flex: 1;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: flex-start;
		align-items: flex-start;
		gap: 1rem;
		padding-bottom: 5rem;
	}
	.col {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: stretch;
		gap: 1rem;
		border: 1px dashed var(--colors-ultra-high);
		padding: 1rem;
	}
	.badge-row {
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}
</style>
