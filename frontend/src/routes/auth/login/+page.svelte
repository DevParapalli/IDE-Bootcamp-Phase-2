<script>
    let email = '';
    
    function handleSubmit() {
        // Handle form submission
        console.log(email);
    }
</script>

<form on:submit={handleSubmit}>
    <label for="email">Email:</label>
    <input type="email" id="email" bind:value={email} required>
    <button type="submit">Login</button>
</form>
