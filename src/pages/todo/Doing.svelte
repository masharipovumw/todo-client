<script>
    import axios from "axios"
    import Loader from "../Loader.svelte"
    import DoingTable from "./DoingTable.svelte"
    import Navigate from "./Navigate.svelte"
    let user = JSON.parse(localStorage.getItem('user'))    

    let Todos = []
  const myTodos = async () => {
  Todos = []
    const response = await axios.get('https://gusty-ahead-comb.glitch.me/api/v1/todos',{
      headers :{
        'authorization': user.token
      }
    })

    Todos = response.data.Todos.filter(todo => todo.isCompleted == true)
    console.log(Todos)
    console.log(Todos.isCompleted);
}
myTodos()


    </script>
    <main>
        <div class="d-flex " style="height: 100vh;">
            <Navigate/>
            <div class="main_section">
              <img src="../images/Doing.jpg" alt="" class="background">
              <div class="content_section">
                <div class="content">
                  <h1>I do it</h1>
                </div>
    
                <div class="table_section">
                  <!-- {#if Todos.length == 0}   -->
                  <!-- <Loader/> -->
                    <!-- {:else} -->
                      <DoingTable/>
                  <!-- {/if} -->
                    </div>
              </div>
            </div>
        </div>
    </main>
    <style>
      .main_section{
        position: relative;
        width: 1256px;
        height: 100vh;
      }
      .background{
        width: 100%;
        height: 100%;
        opacity: 0.6;
        object-fit: cover;
        background-repeat: no-repeat;
    
      }
      .content_section{
        position: absolute;
        width: 90%;
        height: 90%;
        top: 10px;
        left: 20px;
      }
      .content{
        display: flex;
        justify-content: space-between;
      }
      .table_section{
        padding-top: 50px;
        width: 90%;
        height: 90%;
      }
    </style>