<main>
    <div class="users_section">
        <div class="user_avatar">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTba4wmYeOWgJhaD4_tqCAYl2Q5G-OJWQ1ywQ&usqp=CAU" alt="avatar" class="img">
        </div>
        <div class="user_comment">
            <p>I use this app when I fly in a plane or in a car. <br> In short, the app is always handy</p>
            <img src="./images/stars.png" alt="star" class="star">
        </div>
    </div>
</main>
<style>
.users_section{
    display: flex;
    align-items: center;
    width: 400px;
    padding: 5px    ;
    box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);
}
.user_avatar{
    height: 80px;
    width: 80px;
    margin-right: 15px;

}
.img{
    height: 100%;
    width: 100%;
    border: 2px solid rgb(188, 102, 102);
    border-radius: 50%;
}
.user_comment{
    height:100px;
}
.star{
    height: 33px;
    width: 80px;
    padding-bottom: 20px;
    object-fit: cover;
}
</style>