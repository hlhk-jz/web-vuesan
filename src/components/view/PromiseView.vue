<template>
    <button @click="requests">请求</button>
</template>

<script setup>
    /* eslint-disable no-unused-vars */
    //异步请求传统方式，回调地狱
    /*function req(callbak) {
        setTimeout(()=>{
            callbak(200,"成功","我是数据")
        },3000)
    }
    function requests() {
        req((code,msg,data)=>{
            if(code==200){
               console.log("请求成功：",data)
                //如果还有其它请求，就会嵌套
                req((code,msg,data)=>{
                    if(code==200){
                        console.log("请求成功：",data)
                    }else {
                        console.log("请求失败：",msg)
                    }
                })
            }else {
                console.log("请求失败：",msg)
            }
        })
    }*/

   /* function sync1(resolve,reject) {
        setTimeout(()=>{
            resolve("成功")
            //reject("失败")
        },2000)
    }
    function sync2(resolve,reject) {
        setTimeout(()=>{
            resolve("成功2")
            //reject("失败")
        },3000)
    }
    function sync3(resolve,reject) {
        setTimeout(()=>{
            resolve("成功3")
            //reject("失败")
        },3000)
    }*/
    //Promise 解决地狱回调
   /* function requests() {
        new Promise((resolve,reject)=>{
            sync1(resolve,reject)
           // reject("失败")
        }).then((v)=>{
            console.log("请求成功：",v)
            //成功后再创建一个 Promise 执行其它异步请求
            return new Promise((resolve,reject)=>{
                sync2(resolve,reject)
            })
        }).then((v)=>{
            console.log("请求成功2：",v)
            return new Promise((resolve,reject)=>{
                sync3(resolve,reject)
            })
        }).then((v)=>{
            console.log("请求成功3：",v)
        }).catch((e)=>{
            console.log("返回失败：",e)
        })
    }*/

  /*  function requests() {
        request("http://").then((v)=>{
            console.log("请求成功：",v)
            //如果还有其它请求可以在下面写,需要return
            return request("http://")
        }).catch((e)=>{
            console.log("请求失败：",e)
        })
    }*/
   //改造使用 Promise 方法，通用请求方法
    function request(url) {
        return new Promise((req,err)=>{
            setTimeout(()=>{
                //模拟网络请求
                if(url){
                    //调用地址成功
                    req("我是成功数据")
                }else {
                    err("500")
                }
            },3000)
        })
    }

    /**
     * 使用 async 和 await 方式调用，可以像同步方法一样编写请求，就不用写 then 了
     * 使用 await 后，当成功了自动把 Promise 的成功数据赋值给变量，当请求失败了就
     * 会被 catch 捕获
     */
    async function requests() {
        try {
            let rep = await request("http://");
            console.log("1===========",rep)
            rep = await request(null);
            console.log("2===========",rep)
        }catch (e) {
            console.log(e)
        }
    }
</script>