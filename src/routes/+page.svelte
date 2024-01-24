<script lang="ts">
	import profile from '$lib/assets/karsten-winegeart-uNVjLyA3xu8-unsplash.jpg';
	// @ts-ignore
	import { BellIcon, ListFilterIcon } from 'lucide-svelte';

	import { Avatar, WidgetPlaceholder, Skeleton } from 'flowbite-svelte';
	import Chart from '$lib/components/Chart.svelte';
	import Radar from '$lib/components/Radar.svelte';
	import Line from '$lib/components/Line.svelte';
	import { navigating } from '$app/stores';

	export let data;
</script>


{#if $navigating}
	<div class=" space-y-8">
		<Skeleton />
		<WidgetPlaceholder />
	</div>
{:else}
	<div class=" w-[95%] pb-10">
		
		<div class="  flex w-full space-x-14">
			<div class=" w-[70%]">
				<h1 class=" font-bold text-4xl uppercase">market strategy analysis platform</h1>

				<div class=" flex w-full items-start justify-between space-x-6 pt-10">
					<div class=" w-[50%]">
						<Line values={data.data} two={data.two} three={data.three} four={data.four} five={data.five} />
					</div>
					<div class=" w-[50%] translate-x-2">
						<Chart values={data.data} two={data.two} three={data.three} four={data.four} five={data.five} />
					</div>
				</div>
			</div>
			<div class=" mt-10 w-[30%]">
				<h1 class=" text-2xl font-semibold">Statistics</h1>
				<br />
				<Radar bundle={data.bundle} family={data.family} premium={data.premium} />
			</div>
		</div>
	</div>
{/if}
