<script lang="ts">
	import Fuse from 'fuse.js';
	import Bolt from '$lib/components/icons/Bolt.svelte';
	import { onMount, getContext } from 'svelte';
	import { settings, WEBUI_NAME } from '$lib/stores';
	import { WEBUI_VERSION } from '$lib/constants';

	const i18n = getContext('i18n');

	export let suggestionPrompts = [];
	export let className = '';
	export let inputValue = '';
	export let onSelect = (e) => {};

	let sortedPrompts = [];

	const fuseOptions = {
		keys: ['content', 'title'],
		threshold: 0.5
	};

	let fuse;
	let filteredPrompts = [];

	// Initialize Fuse
	$: fuse = new Fuse(sortedPrompts, fuseOptions);

	// Update the filteredPrompts if inputValue changes
	// Only increase version if something wirklich geändert hat
	$: getFilteredPrompts(inputValue);

	// Helper function to check if arrays are the same
	// (based on unique IDs oder content)
	function arraysEqual(a, b) {
		if (a.length !== b.length) return false;
		for (let i = 0; i < a.length; i++) {
			if ((a[i].id ?? a[i].content) !== (b[i].id ?? b[i].content)) {
				return false;
			}
		}
		return true;
	}

	const getFilteredPrompts = (inputValue) => {
		if (inputValue.length > 500) {
			filteredPrompts = [];
		} else {
			const newFilteredPrompts =
				inputValue.trim() && fuse
					? fuse.search(inputValue.trim()).map((result) => result.item)
					: sortedPrompts;

			// Compare with the oldFilteredPrompts
			// If there's a difference, update array + version
			if (!arraysEqual(filteredPrompts, newFilteredPrompts)) {
				filteredPrompts = newFilteredPrompts;
			}
		}
	};

	$: if (suggestionPrompts) {
		sortedPrompts = [...(suggestionPrompts ?? [])].sort(() => Math.random() - 0.5);
		getFilteredPrompts(inputValue);
	}
</script>

{#if filteredPrompts.length === 0}
	<div
		class="mb-2 flex gap-1 text-[13px] font-semibold items-center text-[#0578B8] dark:text-blue-400"
	>
		<div
			class="flex w-full {$settings?.landingPageMode === 'chat'
				? ' -mt-1'
				: 'text-center items-center justify-center'} self-start text-[#0578B8] dark:text-blue-400"
		>
			{$WEBUI_NAME} ‧ v{WEBUI_VERSION}
		</div>
	</div>
{/if}

<div class="w-full">
	{#if filteredPrompts.length > 0}
		<div role="list" class="flex flex-wrap items-center justify-center gap-3 {className}">
			{#each filteredPrompts as prompt, idx (prompt.id || `${prompt.content}-${idx}`)}
				<button
					role="listitem"
					class="waterfall inline-flex items-center gap-2 px-4 py-2 rounded-[4px]
					       border border-[#8ED1FC] dark:border-blue-900
					       bg-white dark:bg-gray-900 hover:bg-[#0693E3]/14 dark:hover:bg-blue-900/30
					       transition group cursor-pointer"
					style="animation-delay: {idx * 60}ms"
					on:click={() => onSelect({ type: 'prompt', data: prompt.content })}
				>
					<Bolt className="size-4 text-[#0578B8] dark:text-blue-400 shrink-0" />
					<span
						class="text-sm font-bold text-[#0578B8] dark:text-blue-300 transition whitespace-nowrap"
					>
						{#if prompt.title && prompt.title[0] !== ''}
							{prompt.title[0]}
						{:else}
							{prompt.content.length > 30 ? prompt.content.slice(0, 30) + '...' : prompt.content}
						{/if}
					</span>
				</button>
			{/each}
		</div>
	{/if}
</div>

<style>
	/* Waterfall animation for the suggestions */
	@keyframes fadeInUp {
		0% {
			opacity: 0;
			transform: translateY(20px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.waterfall {
		opacity: 0;
		animation-name: fadeInUp;
		animation-duration: 200ms;
		animation-fill-mode: forwards;
		animation-timing-function: ease;
	}
</style>
