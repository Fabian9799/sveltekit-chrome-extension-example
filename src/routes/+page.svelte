<script lang="ts">
	import { onMount } from 'svelte';

	let items: chrome.history.HistoryItem[] = [];

	onMount(async () => {
		window.chrome.history
			.search({
				text: 'svelte',
				maxResults: 5
			})
			.then((result) => {
				items = result;
			});
	});
</script>

{#each items as { title, url }}
	<a href={url}>{title}</a>
	<br />
{/each}

<pre>{JSON.stringify(items, null, 2)}</pre>
