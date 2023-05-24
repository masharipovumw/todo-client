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


let TitleInput

const AddList = async () => {
  let body ={
    title : TitleInput.value
  }
const response = await axios.post('https://gusty-ahead-comb.glitch.me/api/v1/todos', body,{
  headers:{
    'authorization':user.token
  }
})
// navigate('/todo')
myTodos()
console.log(response);


}

</script>

<main>
    <button type="button" class="btn bg-info-subtle" data-bs-toggle="modal" data-bs-target="#exampleModal">Add goal</button>
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h1 class="modal-title fs-5" id="exampleModalLabel">Modal title</h1>
              <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <div class="input-group input-group-sm mb-3">
                    <span class="input-group-text" id="inputGroup-sizing-sm">Title</span>
                    <input bind:this ={TitleInput} type="text" class="form-control" placeholder="do homework" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-sm">
                </div>
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
              <button type="button" class="btn btn-primary" on:click={AddList}>Save changes</button>
            </div>
          </div>
        </div>
      </div>
</main>