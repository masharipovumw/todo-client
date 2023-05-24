<script>
    import { Link, navigate } from "svelte-navigator"

    let user = JSON.parse(localStorage.getItem('user'))

    let buyPro = () =>{
        if(!user){
            navigate('/register')
        }else{
            navigate('/todo')
        }
    }

</script>

<main>
    <div class="banner_page">
        <div class="add_section">
            <h1>join our site and try for free. We make your life easier. <br> Make a plan with us</h1>
        </div>
        <div class="login_section">
            <button class="btn_main">
                <Link to="/register"  style="color: aliceblue; text-decoration: none;">
                    Sign up
                </Link>
            </button>
        </div>
        <div class="image_section">
            <img class="img" src="./images/todolist.png" alt="to do list ">
        </div>
    </div>
    <div class="main_banner">
        <div class="left_banner">          
            <div class="text_section">
                <h1>buy pro version, upload <br>video, audio and text notes</h1>
                <div class="login_section">
                    <button class="btn_buy" on:click={buyPro}><h2> Buy PRO</h2></button>
                </div>
            </div>
        </div>
        <div class="right_banner">
            <div class="img_section">
                <img src="./images/pro.png" alt="pro" class="image">
            </div>
        </div>
    </div>
</main>
<style>
    .banner_page{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        margin-bottom: 100px;
    }
    .login_section{
        margin: 30px 0;
    }
	.btn_main{
		width: 200px;
		height: 50px;
		border: none;
        color: aliceblue;
		background-color: rgb(138, 7, 50);
        border-radius: 8px;
	}
	.btn_buy{
		width: 200px;
		height: 50px;
		border: none;
        color: aliceblue;
		background-color: rgb(138, 7, 50);
        border-radius: 8px;
	}
    .main_banner{
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 200px;
        gap: 20px;
    }
    .image{
        height: 150px;
    }
</style>