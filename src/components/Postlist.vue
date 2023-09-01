<script setup>
import axios from 'axios';
import {ref, onMounted} from 'vue'
import Navmenu from './Navmenu.vue';


const postlist = ref([])
const getpostlists = () =>{
    axios.get('https://basic-blog.teamrabbil.com/api/post-newest')
    .then(res => postlist.value = res.data)
    .catch(error = console.log(error))
}
onMounted(() => getpostlists())
</script>

<template>
    <Navmenu/>
    <div class="container mt-5">
        <div class="row">
            <div class="col-4" v-for="(post,index) in postlist" :key="index">
                <!-- <template></template> -->
                <div class="card" style="width: 18rem;">
                <img :src="post.img" class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">{{ post.title }}</h5>
                        <p class="card-text">{{ post.short }}</p>
                        <a href="#" class="btn btn-primary">Go somewhere</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
