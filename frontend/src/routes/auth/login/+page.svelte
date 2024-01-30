<script lang="ts">
	import { goto } from '$app/navigation';


    import type { PageData } from './$types';

    export let data: PageData;

    let email = '';
    let password = '';

    async function handleSubmit() {
        // Handle form submission
        console.log(email);

        const { data:user, error } = await data.supabase.auth.signInWithPassword({
            email: email,
            password: password,
        });

        if (error) {
            console.error(error);
        } else {
            console.log('User signed in:', user);
            goto('/dashboard');
        }
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <label for="email">Email:</label>
    <input type="email" id="email" bind:value={email} required>

    <label for="password">Password:</label>
    <input type="password" id="password" bind:value={password} required> <!-- Added password input field -->

    <button type="submit">Send Magic Link</button>
</form>
