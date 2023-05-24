<script>
    import Footer from "../footer/Footer.svelte"
import BannerPage from "./BannerPage.svelte"
    import Firstuser from "./users/Firstuser.svelte"
    import SecondUser from "./users/SecondUser.svelte"
    import Users from "./users/users.svelte"
	import {Link}from 'svelte-navigator'

</script>

<main>
	<div class="container">
		<div class="header">
			<div class="header_top">
				<div class="logo_section">
					<img src="./images/logo.png" class="logo" alt="logo">
				</div>
				<div class="navbar">
					<li class="nav_link">preference</li>
					<li class="nav_link">PRO</li>
					<div class="login_section">
						<button class="btn_top">
							<p class="title">
								<Link to="/register"  style="color: aliceblue; text-decoration: none;">
									Sign up
								</Link>
							</p>
						</button>
					</div>
				</div>

			</div>
			<div class="header_banner">
				<BannerPage/>
			</div>
			<h1 class="section">Our users opinion</h1>
			<div class="user_coments">
				<div class="user_comment">
					<Users/>
				</div>
				<div class="user_comment">
					<Firstuser/>
				</div>
				<div class="user_comment">
					<SecondUser/>
				</div>
			</div>
		</div>
	</div>
	<div style="margin-top: 50px;">
		<Footer/>
	</div>
</main>
<style>
	.header_top{
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.navbar{
		display: flex;
		align-items: center;
		gap: 50px
	}
	.logo{
		width: 150px;
		height: 120px;
	}
	.btn_top{
		width: 100px;
		height: 30px;
		border: none;
		background-color: rgb(184, 184, 13);
		border-radius: 8px;
		color: aliceblue;
	}
	.header_banner{
		margin-top: 20px;
	}
	.section{
		margin: 50px 0;
	}
	.user_coments{
		display: flex;
		gap: 30px;
	}
</style>