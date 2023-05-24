<script>
    import { navigate } from "svelte-navigator"

    export let isAdmin = false

    const user = JSON.parse(localStorage.getItem('user'))

    // null
    if (user == null) {
        navigate('/')
    }
    else if (isAdmin == true && user.role != 'admin') {
        navigate('/login')
    }
</script>

<slot></slot>