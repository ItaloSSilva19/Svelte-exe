<!-- Assignment -->
<!--	Add a password input field and save the user input in a variable. -->
<!--	Output "Too short" if the password is shorter than 5 characters and "Too long" if it's longer than 10. -->
<!--	Output the password in a paragraph tag if it's between these boundaries. -->
<!--	Add a button and let the user add the passwords to an array. -->
<!--	Output the array values (= passwords) in a unordered list (ul tag). -->
<!--	Bonus: If a password is clicked, remove it from the list. -->

<script>
	let userPassword= '';
	let passwordArray=[];
	
	function addPassword (){
		passwordArray = [
			...passwordArray, userPassword
		];
		console.log(passwordArray);
	}
	function removePassword(index) {
    passwordArray = passwordArray.filter((pass, idx) => {
      return idx !== index;
    });
	}
</script>

<label for="password">Password</label>
<input type="password" bind:value={userPassword}/>

<div>
	{#if userPassword.length < 5}
		<button on:click={addPassword} disabled>Add password </button>
		<p>The password is too short</p>
	{:else if userPassword.length > 10}
		<button on:click={addPassword} disabled>Add password</button>
		<p>The password is too long</p>
	{:else}
		<button on:click={addPassword}>Add password</button>
		<p>The password is: {userPassword}</p> 
	{/if}
</div>

<div>
	{#if passwordArray.length > 0}
		<h2>Password List:</h2>
		<ul type = "square">
			{#each passwordArray as pass, i (pass)}
				<li on:click={removePassword.bind(this, i)}>{pass}</li>
			{/each}
		</ul>
	{/if}	
</div>

<style>
	div {
		position: relative;
		padding-bottom: 15px;
	}
	li {
		font-size: 14px;
		margin-left: 10px;
		list-style-type: square;
		position: relative;
		left: 20px;
	}
</style>

