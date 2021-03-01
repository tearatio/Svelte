<script>
	let password = {pass: '', id: ''}
	let array = []
	
	function passHandler() {
		
		if (password.pass.length >= 5 && password.pass.length <=10) {array = [...array, 
			{pass: this.password, id: Math.random()}
		]
		}
		
		password.pass = ''
	}
</script>

<main>
	<div>
		<input type="password" bind:value="{password.pass}">
		{#if password.pass.length < 5}
			<p>Too short</p>
			{:else if password.pass.length > 10}
			<p>Too long</p> 
	{:else} <p>{password.pass}</p>
		{/if}
	</div>
	<button on:click="{passHandler}">Save password to the array</button>
	<hr>
	<div>
		The enetered passwords are the following: {#each array as item}
			<ul>{item.pass}</ul>
			{console.log(item.pass)}
		{/each}
	</div>
</main>

