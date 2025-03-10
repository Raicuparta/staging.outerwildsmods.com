<script lang="ts">
	import PageContainer from '$lib/components/page-container.svelte';
	import LinkButton from '$lib/components/button/link-button.svelte';
	import PageSectionTitle from '$lib/components/page-section/page-section-title.svelte';
	import DownloadsChart from '$lib/components/downloads-chart/downloads-chart.svelte';
	import type { HistoryPoint } from '$lib/helpers/api/history-points';
	import type { PageData } from './$types';
	import { listedImageSize } from '$lib/helpers/constants';
	import type { ModsRequestItem } from '../../../api/mods.json/+server';

	export let data: PageData;
	const { modDownloadHistory, mod, modList } = data;

	let compareWithMod: ModsRequestItem | null = null;
	let compareWithHistory: HistoryPoint[] = [];

	$: (async () => {
		if (compareWithMod) {
			const modDownloadhistoryResponse = await fetch(
				`/api/${compareWithMod.uniqueName}/downloads.json`
			);

			if (modDownloadhistoryResponse.ok) {
				compareWithHistory = await modDownloadhistoryResponse.json();
			}
		} else {
			compareWithHistory = [];
		}
	})();

	const modsExceptSelf = modList.filter(({ uniqueName }) => uniqueName !== mod.uniqueName);
</script>

<PageContainer
	title="{mod.name} - Downloads Chart - Outer Wilds Mods"
	description="Download history graph for the Outer Wilds Mod '{mod.name}'"
	imageUrl={mod.openGraphImageUrl ?? mod.imageUrl}
	imageWidth={listedImageSize.width}
	imageHeight={listedImageSize.height}
>
	<div>
		<div class="flex mb-4">
			<LinkButton href=".." isSmall>‹ Back to {mod.name}</LinkButton>
		</div>
		<PageSectionTitle id="downloads">{mod.name} downloads over time</PageSectionTitle>
		<div class="mb-2">
			<span>Compare with:</span>
			<select
				class="input w-full py-0"
				on:change={(event) => {
					compareWithMod =
						modsExceptSelf.find((mod) => mod.uniqueName === event.currentTarget.value) || null;
				}}
			>
				<option value={null}>None</option>
				{#each modsExceptSelf as mod}
					<option value={mod.uniqueName}>{mod.name}</option>
				{/each}
			</select>
		</div>
		<DownloadsChart
			historyPoints={modDownloadHistory}
			comparePoints={compareWithHistory}
			{mod}
			{compareWithMod}
		/>
	</div></PageContainer
>
