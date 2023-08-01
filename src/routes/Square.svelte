<script lang="ts">
	import { get_twemoji_url } from './utils';
	import { send } from './transitions';

	export let emoji: string;
	export let selected: boolean;
	export let found: boolean;
	export let group: 'a' | 'b';
</script>

<div class="square" class:flipped={selected || found}>
	<button on:click disabled={selected || found} />

	<div class="background" />

	{#if !found}
		<img out:send={{ key: `${emoji}:${group}` }} src={get_twemoji_url(emoji)} alt={emoji} />
	{/if}
</div>

<style>
	.square {
		display: flex;
		justify-content: center;
		align-items: center;
		transform-style: preserve-3d;
		transition: transform 0.4s;
	}

	.flipped {
		transform: rotateY(180deg);
	}

	.background {
		position: absolute;
		width: 100%;
		height: 100%;
		background: white;
		border: 0.5em solid #eee;
		transform: rotateY(180deg);
		backface-visibility: hidden;
		border-radius: 1em;
	}

	button {
		position: absolute;
		width: 100%;
		height: 100%;
		backface-visibility: hidden;
		background: #eee;
		border: none;
		border-radius: 1em;
		font-size: inherit;
	}

	img {
		display: block;
		width: 6em;
		height: 6em;
		pointer-events: none;
		transform: rotateY(180deg);
		backface-visibility: hidden;
	}
</style>
