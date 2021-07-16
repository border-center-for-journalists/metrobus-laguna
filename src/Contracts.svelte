<script>
	export let contracts;
</script>
<main>
	{#each contracts as contract}
	<a href='' class='article'>
		<nav>
			<i class='material-icons'>download</i>
		</nav>
		<content>
			<p class='title'>{contract.concept}</p>
			<p class='company'>{contract.company}</p>
			<p class='ammount'>{contract.ammount}</p>
		</content>
	</a>
	{/each}
</main>
<style>
	main{
		display: flex;
		flex-flow: row wrap;
		max-width: 1150px;
		margin: 0 auto;
	}
	.article{
		display: flex;
		color: white;
		padding: 8px 15px;
		border:  3px solid #787878;
		border-radius: 5px;
		margin: 25px 25px 0 0;
		flex: 0 1 calc(33% - 49px);
	}
	.article:nth-child(3n){
		margin-right: 0;
	}
	.article nav{
		padding: 5px 7px 0 5px;
	}
	.article nav i{
		font-size: 24px;
	}
	.title{
		font-size: 12px;
		margin:  0 auto;
	}
	.company{
		font-size: 17px;
		line-height: 28px;
		text-transform: uppercase;
		margin: 5px 0;
	}
	.ammount{
		font-size:  17px;
		color: #FE4940;
		margin: 0;
	}
</style>