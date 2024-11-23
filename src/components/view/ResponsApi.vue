
<template>
    <div>
        <h1>我是响应式API</h1>
        <div>
            <h3>{{ count }}</h3>
            <button @click="cliCount">增加count</button>
        </div>
    </div>
</template>

<script>
    //import { ref, reactive, readonly } from 'vue'
    //ref对象和基本数据类型都可以，reactive适合对象，readonly定义后不可修改
    import { ref} from 'vue'
    export default {
       setup(){
           const count = ref(0);
           function cliCount() {
               count.value+=1
           }
           return { count,cliCount };
       }
    }
</script>

