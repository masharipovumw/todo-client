<script>
	import {Route, Router} from 'svelte-navigator'
    import Mainpage from './pages/Main/Mainpage.svelte'
    import LoginPage from './pages/login/Login_page.svelte'
    import TodoPade from './pages/todo/TodoPade.svelte'
    import Comp from './pages/todo/Comp.svelte'
    import Doing from './pages/todo/Doing.svelte'
    import Register from './pages/login/Register.svelte'
    import RoleProtector from './RoleProtector.svelte'
</script>

<Router>
	<Route path='/' primary={false}>
		<Mainpage/>
	</Route>
	<Route path='/register' primary={false}>
		<LoginPage/>
	</Route>
	<Route path='/login' primary={false}>
		<Register/>
	</Route>
	<Route path='/todo' primary={false}>
		<RoleProtector>
			<TodoPade/>
		</RoleProtector>
	</Route>
	<Route path='/todo/completed' primary={false}>
		<RoleProtector>
			<Comp />
		</RoleProtector>
	</Route>
	<Route path='/todo/doing' primary={false}>
		<RoleProtector>
			<Doing />
		</RoleProtector>
	</Route>
</Router>