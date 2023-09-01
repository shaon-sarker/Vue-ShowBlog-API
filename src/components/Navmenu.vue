<script setup>
import axios from 'axios';
import {ref, onMounted} from 'vue'

const navemenu = ref([])
const getnavemnus = () =>{
    axios.get('https://basic-blog.teamrabbil.com/api/post-categories')
    .then(res => navemenu.value = res.data)
    // .catch(error = console.log(error))
}
onMounted(() => getnavemnus())
</script>


<template>
<nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container">
            <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav m-auto">
                        <li class="nav-item" v-for="menu in navemenu" :key="menu.id">
                        <a class="nav-link active" aria-current="page" href="#">{{ menu.name }}</a>
                        </li>
                    </ul>
                </div>
    </div>
</nav>
</template>