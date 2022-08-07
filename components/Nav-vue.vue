<template>
    <div>
        <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal">
            <el-menu-item index="index" keyPath="/"><router-link to="/">Главная</router-link></el-menu-item>
            <el-menu-item index="login" keyPath="/login"><router-link to="/login">Авторизация</router-link></el-menu-item>
            <el-menu-item index="shop" keyPath="/shop"><router-link to="/shop">Магазин</router-link></el-menu-item>
        </el-menu>
    </div>
</template>

<script>
  export default {
    data() {
      return {
            activeIndex: 'index',
            activeIndex2: 'login'
      };
    },
    methods: {
    }
  }
</script>