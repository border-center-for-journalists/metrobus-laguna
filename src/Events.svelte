<script>
	export let events;
</script>
<div class='container'>
	{#each events as event}
	<article><!-- 
		<i style="border-bottom:10px solid #{event.color}"></i> -->
		<nav style="background-color: #{event.color}">{event.letter}</nav>
		<content>
			<p class='date'>{event.date}</p>
			<p>{event.text}</p>
		</content>
	</article>
	{/each}
</div>

<style>
	.container{
		display: flex; 
		flex-flow: row wrap;
		max-width: 1150px;
		margin: 0 auto;
	}
/*	.container::before{
		position: absolute;
		left: 15px;
		width: 1px;
		height: 100%;
		background-color: #5f5f5f;
		content: '';
	}*/
	article{
		background-color: #363636;
		display: flex;
		margin: 25px 25px 0 0;
		color: white;
		font-size: 13px;
		position: relative;
		flex: 0 1 calc(33% - 13px);
	}

	article:nth-child(3n){
		margin-right: 0;
	}
	/*
	article i{
		content: '';
		width: 0; 
		height: 0; 
		border-left: 10px solid transparent;
		border-right: 10px solid transparent; 
		border-bottom:10px solid #FF4840;
		position: absolute;
		top: -10px;
		left: 10px; 
	}
	article::after{
		content: '';
		width: 10px;
		height: 10px;
		border-radius: 50%;
		background-color: #5f5f5f;
		position: absolute;		
		top: -20px;
		left: 24px;
	}
	*/
	article nav{
		background-color: #FF4840;
		text-align: center;
		font-size: 30px;
		font-weight: bold;
		padding: 0 14px;
		align-items:center;
        justify-content:center;
        display: flex;
        text-transform: uppercase;
        width: 17px;
	}
	article content{
		margin: 12px 15px;
		font-size: 13px;
	}
	article p{
		margin: 2px 0 8px;
	}
	article .date{
		color: #B0B0B0;
		text-transform: uppercase;
		font-size: 12px;
	}
</style>