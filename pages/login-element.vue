<template>
    <div class="common-layout">
        <el-container class="layout-container-demo" v-loading="loading">
            <el-header>Авторизация</el-header>
            <el-main>
                <el-form :model="form" label-width="200px">
                <el-container v-if="this.errors.length > 0">
                    <el-alert v-for="error in this.errors" :key="error" :closable="false"
                        title=""
                        type="error">{{error}}
                    </el-alert>
                </el-container>
                    <el-form-item label="Электронная почта">
                        <el-input v-model="form.email" placeholder="Электронная почта" />
                    </el-form-item>
                    <el-form-item label="Пароль">
                        <el-input
                            v-model.trim="form.password"
                            type="password"
                            placeholder="Пароль"
                            show-password />
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="checkForm">Авторизация</el-button>
                    </el-form-item>
                </el-form>
            </el-main>
        </el-container>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                form: {
                    email: '',
                    password: ''
                },
                errors: [],
                loading: false,
            }
        },
        methods: {
            checkForm(e) {
                this.errors = [];

                if (!this.form.password) {
                    this.errors.push('Введите пароль');
                }

                if (this.form.password.length < 8) {
                    this.errors.push('Пароль не может быть меньше 8 символов');
                }

                if (!this.strWithCapital(this.form.password)) {
                    this.errors.push('Пароль должен содержать хотя бы одну заглавную букву');
                }

                if (!this.form.email) {
                    this.errors.push('Укажите электронную почту.');
                } else if (!this.validEmail(this.form.email)) {
                    this.errors.push('Укажите корректный адрес электронной почты.');
                }

                if (!this.errors.length) {
                    this.loading = true;

                    setTimeout(() => {
                        //Разблокировать форму
                        //Перенаправить на главную страницу
                        this.loading = false;
                    }, 2000);
                    return true;
                }
            },
            validEmail: function (email) {
                var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
                return re.test(email);
            },
            strWithCapital: function(str){
                return /[A-Z]/.test(str)
            }
        }
    }
</script>

<style>
    .el-header {
        position: relative;
        background-color:#409EFF;
        color: white;
        font-size: 2em;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>