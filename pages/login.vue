<template>
    <div>
        <h1>Авторизация</h1>
        <form @submit="userLogin">
            <div>
                <label>Электронная почта</label>
                <input type="email" v-model="login.mail">
            </div>
            <div>
                <label>Пароль</label>
                <input type="password" v-model="login.password" minlength="8">
            </div>
            <el-button type="primary" plain>Авторизация</el-button>
        </form>
    </div>
    
    
</template>
<script>
    export default {
        data() {
            return {
                login: {
                    mail: '',
                    password: ''
                }
            }
        },
        methods: {
            userLogin() {
                console.log('login');
            }
        }
    }
    
</script>