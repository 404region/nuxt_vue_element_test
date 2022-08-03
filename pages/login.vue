<template>
    <div>
        <h1>Авторизация</h1>
        <form @submit="userLogin">
            <div>
                <label>Электронная почта</label>
                <input type="email" v-model="login.email" required>
            </div>
            <div>
                <label>Пароль</label>
                <input type="password" v-model="login.password" minlength="8" required>
            </div>
            <button type="primary" plain>Авторизация</button>
        </form>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                element: {
                    email: '',
                    password: ''
                },
                login: {
                    email: '',
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