<template>
    <div>
        <component :is="currentComponent"></component>
        <button @click="show('ComponentA')">A</button>
        <button @click="show('ComponentB')">b</button>
        <button @click="show('ComponentC')">c</button>
    </div>
</template>

<script>
    import { h,ref } from 'vue';

    const ComponentA = () => {
        return h('div', 'Hello, ComponentA 3!');
    };
    const ComponentB = () => {
        return h('div', 'Hello, ComponentB 3!');
    };
    const ComponentC = () => {
        return h('div', 'Hello, ComponentC 3!');
    };

    /**
     * component 内置组件可以控制组件的显示和隐藏，
     * 配合方法可以控制多个不同的组件动态切换
     */
    // ref('ComponentA'); 这里的ComponentA要和组件名称一样才会显示
    export default {
        setup(){
            const currentComponent = ref('ComponentA');

            function show(r) {
                currentComponent.value= r;
            }
            return {currentComponent,show}
        },
        components:{
            ComponentA,ComponentC,ComponentB
        }
    }
</script>