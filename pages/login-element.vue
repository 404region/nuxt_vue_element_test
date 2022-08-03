<template>
    <div class="common-layout">
        <el-container class="layout-container-demo">
            <el-header>Авторизация</el-header>
            <el-main>
                <el-form :model="form" label-width="200px">
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
            }
        },
        methods: {
            checkForm(e) {
                this.errors = [];
                console.log('submit!');

                if (!this.form.password) {
                    this.errors.push('Введите пароль');
                }

                if (!this.form.email) {
                    this.errors.push('Укажите электронную почту.');
                } else if (!this.validEmail(this.form.email)) {
                    this.errors.push('Укажите корректный адрес электронной почты.');
                }
                console.log(this.errors);

                if (!this.errors.length) {
                    return true;
                }
            },
            validEmail: function (email) {
                var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
                return re.test(email);
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