<!--登录加密，后端解密-->
<template>
    <div>
        <label>用户名</label>
        <input name="userName" v-model="userName" type="text"/> <br/>
        <label>密码</label>
        <input name="passWord" v-model="passWord" type="password"/>
        <button @click="commitForm">提交</button>
    </div>
</template>

<script setup>
    import CryptoJS from 'crypto-js';
    import axios from 'axios';
    import { ref } from "vue"
    const userName = ref("")
    const passWord = ref("")
    function commitForm() {
        const password = encrypt(passWord.value);
        console.log("userName:",userName.value,"passWord:",password)
        axios.post('http://localhost:9001/cors/logoin', {
            userName: userName.value,
            passWord: password
             })
            .then(response => {
                console.log(response.data);
            })
            .catch(error => {
                console.error('There was an error!', error);
            });
    }

    /** ---密码加密 start--- */
    const SECRET_KEY = CryptoJS.enc.Utf8.parse("a15q8f6s5s1a2v3s");
    const SECRET_IV = CryptoJS.enc.Utf8.parse("a3c6g5h4v9sss3v5");

    function encrypt(pwd) {
        let srcs = CryptoJS.enc.Utf8.parse(pwd);
        let encrypted = CryptoJS.AES.encrypt(srcs, SECRET_KEY, {
            iv: SECRET_IV ,
            mode: CryptoJS.mode.CBC,
            padding: CryptoJS.pad.ZeroPadding
        })
        return CryptoJS.enc.Base64.stringify(encrypted.ciphertext);
    }

</script>