<template>
    <div class="layout">
        <button @click="shows">请求</button>
        <h1>内容：</h1>
    </div>
</template>
<script>
    //import { ref } from 'vue'
    import axios from 'axios'
    export default {
        name: "UserInfo",
        setup(){
            //let name = ref("aaaa");
            const shows=()=>{
                axios.get("http://localhost:9001/cors/test").then((response) => {
                    console.log(response.data)
                })
            }
            return {shows}
        }
    }
</script>