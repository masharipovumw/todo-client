<script>
  import axios from "axios"
  let user = JSON.parse(localStorage.getItem('user'))
  
let Todos = []

const myTodos = async () => {
  Todos = []
    const response = await axios.get('https://gusty-ahead-comb.glitch.me/api/v1/todos',{
      headers :{
        'authorization': user.token
      }
    })
    
    Todos = response.data.Todos.filter(todo => todo.isCompleted == false)
    console.log(Todos);
}
myTodos()

const Dobutton = async (id) => {
    const response = await axios.patch('https://gusty-ahead-comb.glitch.me/api/v1/todos/' + id,{
      headers:{
        'authorization': user.token
      }
    })
    
    myTodos()
  }
const DeleteList = async (id) => {
    const response = await axios.delete('https://gusty-ahead-comb.glitch.me/api/v1/todos/' + id,{
      headers:{
        'authorization': user.token
      }
    })
    
    myTodos()
}
  console.log(user.token)
</script>


<main>
    <table class="table">
        <thead>
          <tr>
            <th scope="col">title</th>
            <th scope="col">position</th> 
            <th scope="col">Action</th> 
          </tr>
        </thead>
        <tbody>
            {#each Todos as todo }    
            <tr>
            <td>{todo.title}</td>
            <td>doing</td>
            <div class="d-flex gap-3">
                <button type="button" class="btn btn-success" on:click={() => Dobutton(todo.id)} >
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-clipboard2-check" viewBox="0 0 16 16">
                    <path d="M9.5 0a.5.5 0 0 1 .5.5.5.5 0 0 0 .5.5.5.5 0 0 1 .5.5V2a.5.5 0 0 1-.5.5h-5A.5.5 0 0 1 5 2v-.5a.5.5 0 0 1 .5-.5.5.5 0 0 0 .5-.5.5.5 0 0 1 .5-.5h3Z"/>
                    <path d="M3 2.5a.5.5 0 0 1 .5-.5H4a.5.5 0 0 0 0-1h-.5A1.5 1.5 0 0 0 2 2.5v12A1.5 1.5 0 0 0 3.5 16h9a1.5 1.5 0 0 0 1.5-1.5v-12A1.5 1.5 0 0 0 12.5 1H12a.5.5 0 0 0 0 1h.5a.5.5 0 0 1 .5.5v12a.5.5 0 0 1-.5.5h-9a.5.5 0 0 1-.5-.5v-12Z"/>
                    <path d="M10.854 7.854a.5.5 0 0 0-.708-.708L7.5 9.793 6.354 8.646a.5.5 0 1 0-.708.708l1.5 1.5a.5.5 0 0 0 .708 0l3-3Z"/>
                </svg>
                </button>
                <button type="button" class="btn btn-danger" on:click={() => DeleteList(todo.id)}>
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16"> 
                    <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5Zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5Zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6Z"/>
                    <path d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1ZM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118ZM2.5 3h11V2h-11v1Z"/>
                </svg>
                </button>
            </div>
            </tr>
            {/each}
        </tbody>
      </table>
</main>