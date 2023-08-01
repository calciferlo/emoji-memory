<script lang="ts">
	import { get_twemoji_url } from './utils';
	import { receive } from './transitions';

	export let found: string[];
</script>

<div class="found">
	{#each found as emoji (emoji)}
		<div class="pair">
			<img in:receive={{ key: `${emoji}:a` }} src={get_twemoji_url(emoji)} alt={emoji} />
			<img in:receive={{ key: `${emoji}:b` }} src={get_twemoji_url(emoji)} alt={emoji} />
		</div>
	{/each}
</div>

<style>
	.found {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 1em;
		height: 100%;
		filter: drop-shadow(0.2em 0.2em 0.5em rgba(0, 0, 0, 0.2));
	}

	.pair {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 5em;
		height: 5em;
		padding: 1em;
		background: white;
		border-radius: 50%;
	}

	img {
		position: absolute;
		width: 2.5em;
		height: 2.5em;
	}
</style>
