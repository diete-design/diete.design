<script lang="ts">
	import table from '$lib/components/ui/table/table.svelte?raw'
	import thead from '$lib/components/ui/table/thead.svelte?raw'
	import tr from '$lib/components/ui/table/tr.svelte?raw'
	import th from '$lib/components/ui/table/th.svelte?raw'
	import tbody from '$lib/components/ui/table/tbody.svelte?raw'
	import td from '$lib/components/ui/table/td.svelte?raw'
	import Code from '$lib/components/custom/code.svelte'
	import TabContent from '$lib/components/custom/tab-bar/tab-content.svelte'
	import { onMount } from 'svelte'
	import ComponentTemplate from '$lib/components/custom/component-template.svelte'
	import CodeComponentTemplate from '$lib/components/custom/code-component-template.svelte'
	import Table from '$lib/components/ui/table/table.svelte'
	import Tr from '$lib/components/ui/table/tr.svelte'
	import Th from '$lib/components/ui/table/th.svelte'
	import Td from '$lib/components/ui/table/td.svelte'

	let tableCss: string = $state('Loading...')
	let theadCss: string = $state('Loading...')
	let trCss: string = $state('Loading...')
	let thCss: string = $state('Loading...')
	let tbodyCss: string = $state('Loading...')
	let tdCss: string = $state('Loading...')

	// Svelte compiler breaks when it finds closing script tag, hence the need to make the template literal to have two parts
	let useCode = $derived(
		`<script lang="ts">
    import Table from '$lib/components/ui/table/table.svelte'
    import THead from '$lib/components/ui/table/thead.svelte'
    import Tr from '$lib/components/ui/table/tr.svelte'
    import Th from '$lib/components/ui/table/th.svelte'
    import TBody from '$lib/components/ui/table/tbody.svelte'
    import Td from '$lib/components/ui/table/td.svelte'
</script` +
			`>

<Table>
    <Tr>
        <Th>Table header</Th>
        <Th>Table header</Th>
        <Th>Table header</Th>
    </Tr>
    <Tr>
        <Td>Table cell</Td>
        <Td>Table cell</Td>
        <Td>Table cell</Td>
    </Tr>
    <Tr>
        <Td>Table cell</Td>
        <Td>Table cell</Td>
        <Td>Table cell</Td>
    </Tr>
</Table>
`,
	)

	onMount(async () => {
		const responseTable = await fetch('/generated/css/ui/table/table.css')
		const responseTHead = await fetch('/generated/css/ui/table/thead.css')
		const responseTr = await fetch('/generated/css/ui/table/tr.css')
		const responseTh = await fetch('/generated/css/ui/table/th.css')
		const responseTBody = await fetch('/generated/css/ui/table/tbody.css')
		const responseTd = await fetch('/generated/css/ui/table/td.css')
		tableCss = await responseTable.text()
		theadCss = await responseTHead.text()
		trCss = await responseTr.text()
		thCss = await responseTh.text()
		tbodyCss = await responseTBody.text()
		tdCss = await responseTd.text()
	})
</script>

{#snippet description()}{/snippet}

{#snippet examples()}
	<Table>
		<Tr>
			<Th>Table header</Th>
			<Th>Table header</Th>
			<Th>Table header</Th>
		</Tr>
		<Tr>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
		</Tr>
		<Tr>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
		</Tr>
	</Table>
{/snippet}

{#snippet controls()}{/snippet}

{#snippet preview()}
	<Table>
		<Tr>
			<Th>Table header</Th>
			<Th>Table header</Th>
			<Th>Table header</Th>
		</Tr>
		<Tr>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
		</Tr>
		<Tr>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
			<Td>Table cell</Td>
		</Tr>
	</Table>
{/snippet}

{#snippet extraSvelte()}
	<TabContent value="table"><Code language="svelte" code={table} /></TabContent>
	<TabContent value="thead"><Code language="svelte" code={thead} /></TabContent>
	<TabContent value="tr"><Code language="svelte" code={tr} /></TabContent>
	<TabContent value="th"><Code language="svelte" code={th} /></TabContent>
	<TabContent value="tbody"><Code language="svelte" code={tbody} /></TabContent>
	<TabContent value="td"><Code language="svelte" code={td} /></TabContent>
{/snippet}

{#snippet extraCss()}
	<TabContent value="table"><Code language="css" code={tableCss} /></TabContent>
	<TabContent value="thead"><Code language="css" code={theadCss} /></TabContent>
	<TabContent value="tr"><Code language="css" code={trCss} /></TabContent>
	<TabContent value="th"><Code language="css" code={thCss} /></TabContent>
	<TabContent value="tbody"><Code language="css" code={tbodyCss} /></TabContent>
	<TabContent value="td"><Code language="css" code={tdCss} /></TabContent>
{/snippet}

{#snippet implement()}
	<CodeComponentTemplate {extraSvelte} {extraCss} />
{/snippet}

<ComponentTemplate
	name="Table"
	tagline=""
	{description}
	{examples}
	{controls}
	{preview}
	{useCode}
	{implement}
/>
