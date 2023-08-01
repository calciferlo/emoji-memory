<script lang="ts">
</script>

<div class="modal-background">
	<div class="modal">
		<slot />
	</div>
</div>

<style>
	.modal-background {
		position: fixed;
		left: 0;
		top: 0;
		display: grid;
		place-items: center;
		height: 100%;
		width: 100%;
		backdrop-filter: blur(10px);
		z-index: 999;
	}
</style>
