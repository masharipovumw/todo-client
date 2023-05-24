<script>
    import axios from 'axios'
    import {Link, navigate}from 'svelte-navigator'
    

    let user = JSON.parse(localStorage.getItem('user'))

    const removeUser = ()=>{
      localStorage.removeItem('user')
      navigate('/')
  }

  const deleteAccount = async () => {
    const response = await axios.delete('https://gusty-ahead-comb.glitch.me/api/v1/account',{
      headers :{
        'authorization': user.token
      }
    })
    navigate('/')
    localStorage.removeItem('user')
}

</script>
<div class="d-flex flex-column flex-shrink-0 p-3 text-bg-dark" style="width: 280px; height: 100vh;">
    <a href="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto text-white text-decoration-none">
      <svg class="bi pe-none me-2" width="40" height="32"><use xlink:href="#bootstrap"></use></svg>
      <span class="fs-4">Sidebar</span>
    </a>
    <hr>
    <ul class="nav nav-pills flex-column mb-auto">
      <li class="nav-item">
        <Link to="/todo/" class="nav-link text-white " aria-current="page">
          <svg class="bi pe-none me-2" width="16" height="16"><use xlink:href="#home"></use></svg>
          All list
        </Link>
      </li>
      <li>
        <Link to="/todo/completed" class="nav-link  text-white">
          <svg class="bi pe-none me-2" width="16" height="16"><use xlink:href="#speedometer2"></use></svg>
          completed
        </Link>
      </li>
      <li>
        <Link to="/todo/doing" class="nav-link text-white">
          <svg class="bi pe-none me-2" width="16" height="16"><use xlink:href="#table"></use></svg>
          I'm doing
        </Link>
      </li>
    </ul>
    <hr>
    <div class="dropdown">
      <a href="/" class="d-flex align-items-center text-white text-decoration-none dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
        <img src="../images/avatar.jpg" alt="" width="32" height="32" class="rounded-circle me-2">
      </a>
      <ul class="dropdown-menu dropdown-menu-dark text-small shadow">
        <li><p class="dropdown-item">{user.name}</p></li>
        <button class="login dropdown-item" on:click={removeUser}>Sign out</button>
        <li><hr class="dropdown-divider"></li>
        <li><a class="dropdown-item text-danger" href="#" on:click={deleteAccount}>Delete the account</a></li>
      </ul>
    </div>
</div>
<style>
  .login{
    border: none;
    background-color: transparent;
  }
</style>
