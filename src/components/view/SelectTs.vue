<template>
    <div>
        <h1>选择器</h1>
        <a href="#">连接</a><br/>
        <text>我是文本</text>
        <ul>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        </ul>
    </div>
</template>
<script>
    /**
     * :active（选中的元素处于活动状态）
     :checked（选中的表单元素）
     :disabled（禁用的表单元素）
     :empty（没有子元素的元素）
     :enabled（可用的表单元素）
     :first-child（第一个子元素）
     :first-of-type（同类型元素的第一个）
     :focus（获取焦点的元素）
     :hover（鼠标悬停的元素）
     :last-child（最后一个子元素）
     :last-of-type（同类型元素的最后一个）
     :not（不满足指定选择器的元素）
     :nth-child(n)（选择第n个子元素）
     :nth-last-child(n)（选择倒数第n个子元素）
     :nth-last-of-type(n)（选择倒数第n个同类型元素）
     :nth-of-type(n)（选择第n个同类型元素）
     :only-child（唯一的子元素）
     :only-of-type（唯一的同类型元素）
     :root（文档的根元素）
     :target（URI指向的目标元素）
     :visited（已访问的链接）
     */
</script>
<style>
    div > a:active{
         color: red;
    }
    div > a:hover{
        color: red;
    }
    div > text:after{
        content: "测试："
    }
    ul > li:nth-child(1){
        color: red;
    }
</style>

