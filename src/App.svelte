<script>
	import LeafletMap from './LeafletMap.svelte';
	import Events from './Events.svelte';
	import Contracts from './Contracts.svelte';
	import * as events from './data/events.json';
	import * as contracts from './data/contracts.json';

	let selectedTab = 'events';
</script>

<main>
	<h1>Metrobús Laguna</h1>
	<h2>la ruta de la corrupción</h2>
	<h3>Lorem ipsum dolor sit amet</h3>
	<div class='container'>
		<LeafletMap events={events.default} contracts={contracts.default} />

		<nav>
			<button class:selected={selectedTab === 'events'} on:click={() => selectedTab = 'events'}>
				<i class='material-icons'>calendar_today</i> Eventos
			</button>
			<button class:selected={selectedTab === 'contracts'}  on:click={() => selectedTab = 'contracts'}>
				<i class='material-icons'>description</i> Contratos
			</button>
		</nav>
		{#if selectedTab === 'events'}
			<Events events={events.default} />
		{/if}
		{#if selectedTab === 'contracts'}
			<Contracts contracts={contracts.default} />
		{/if}
	</div>
</main>

<style>
	h1{
		color: #FF473F;
		font-weight: bold;
		font-size: 51px;
		line-height: 51px;
		margin: 28px 0 0;
	}
	h2{
		font-size: 51px;
		margin: 10px 0;
		line-height: 51px;
		color: white;
		text-align: center;
	}
	h3{
		text-align: center;
		font-size: 15px;
		color: #A3A3A3;
		text-transform: uppercase;
		margin: 0;
		letter-spacing: 2.3px;
	}
	.container{
		max-width: 1150px;
		margin: 43px auto 0;
	}
	nav{
		margin:35px 0 7px;
		display: flex;
	}
	 nav button{
		flex: 1 1 0px;
		background-color: transparent;
		color: white;
		border-bottom: 5px solid #363636;
		text-transform: uppercase;
		font-size: 17px;
		margin: 0;
		padding: 0 0 9px;

	}
	 nav button.selected{
		color: #FF473F;
		border-bottom:  5px solid #FF473F;
	}
	 nav button i{
		font-size: 16px;
		position: relative;
		left:  -4px;
		top: 2px;
	}
</style>