<script>
    import axios from 'axios'
    import { Link, navigate } from 'svelte-navigator'


let nameInput
let userNameInput
let passwordInput

const Register = async () => {
        let body = {
            name : nameInput.value,
            username: userNameInput.value,
            password: passwordInput.value
        }

        let response = await axios.post('https://gusty-ahead-comb.glitch.me/api/v1/account', body)
        localStorage.setItem('user', JSON.stringify(response.data))
        navigate('/todo')
    } 

</script>

<main>
    <div class="main_section" style="height: 100vh;">
        <div class="container"  >
            <div class="input_section">
                <h3> Register </h3>
                <input class="input" bind:this={nameInput} placeholder="name" type="text" style="border-radius: 8px; text-align: center;" >
                <input class="input" bind:this={userNameInput} placeholder="username" type="text" style="border-radius: 8px; text-align: center;" >
                <input class="input" bind:this={passwordInput} placeholder="Password" type="text"  style="border-radius: 8px; text-align: center;">
                <Link to="/login">I've an account</Link>
                <button class="btn btn-primary" on:click={Register}> sign in </button>
            </div>
        </div> 
    </div>
</main>
<style>
    .input{
        height: 30px;
    }
    .main_section{
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .btn{
		width: 100px;
		height: 30px;
		border: none;
		background-color: rgb(184, 184, 13);
		border-radius: 8px;
		color: aliceblue;
	}
    .input_section{
        display: flex;
        align-items: center;
        flex-direction: column;
        gap: 20px;
    }
</style>