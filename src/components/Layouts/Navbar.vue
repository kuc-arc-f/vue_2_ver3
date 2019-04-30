<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="#">Vue_2</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation" >
        <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item active">
                    <router-link  to="/" class="nav-link">Home</router-link>
                </li>
                <li class="nav-item active">
                    <router-link  to="/about" class="nav-link">About</router-link>
                </li>
                <li class="nav-item active">
                    <router-link  to="/users/logout" class="nav-link">Logout</router-link>
                </li>
                <li class="nav-item active">
                    <router-link  to="/users/check" class="nav-link">User-check</router-link>
                </li>
                <!--
                <li class="nav-item active">
                    <router-link  to="/users/new" class="nav-link">User-add</router-link>
                </li>
                -->
                <li class="nav-item active">
                    <router-link  to="/users/login" class="nav-link">Login</router-link>
                </li>
                
                <!--
                <li class="nav-item active">
                    <router-link  to="/todos" class="nav-link">Todos</router-link>
                </li>
                -->
                <li class="nav-item active">
                    <router-link  to="/tasks" class="nav-link">Tasks</router-link>
                </li>
            </ul>
        </div>
        <hr />
    </nav>
</template>

<script>
export default {
  created () {
    /* console.log('AA') */
  }
}
</script>
