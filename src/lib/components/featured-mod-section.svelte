<script lang="ts">
	import LinkButton from '$lib/components/button/link-button.svelte';
	import type { ModsRequestItem } from 'src/routes/api/mods.json/+server';
	import { type SortOrderId, sortOrderParamName } from '$lib/helpers/mod-sorting';
	import ModCard from './mod-grid/mod-card.svelte';

	export let mods: ModsRequestItem[];
	export let sortOrder: SortOrderId;
	export let title: string;

	let href = `/mods?${sortOrderParamName}=${sortOrder}`;
</script>

<div class="m-auto md:w-0 flex-1 flex flex-col gap-2 max-w-full">
	<LinkButton {href}>
		<span class="text-xl">
			{title}
		</span>
	</LinkButton>
	{#each mods as mod (mod?.uniqueName)}
		<ModCard hideDescription {mod} />
	{/each}
	<div class="flex flex-col justify-center">
		<LinkButton isSmall {href}>
			More {title}...
		</LinkButton>
	</div>
</div>
