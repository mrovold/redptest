<template>
  <div class="b-form__wrapper">
        <b-form class="b-form" @submit.stop.prevent>
            <label class="sr-only" for="inline-form-input-name">Логин</label>
            <b-input-group class="mb-2 mr-sm-2 mb-sm-0">
                <b-form-input value="" id="inline-form-input-username" placeholder="Пользователь" v-model="username"></b-form-input>
            </b-input-group>
            

            <label class="sr-only" for="inline-form-input-username" input v-model="password">Пароль</label>
            <b-input-group prepend="" class="mb-2 mr-sm-2 mb-sm-0">
                <b-button class="button" variant="outline-secondary" @click="toggleShow">
                    <b-icon v-if="showPassword" icon="eye-fill" v-model="password"></b-icon>
                    <b-icon v-else icon="eye-slash-fill" v-model="password"></b-icon>
                </b-button>
                <b-form-input value="" v-if="showPassword" type="text" v-model="password"  id="inline-form-input-name" class="mb-2 mr-sm-2 mb-sm-0"></b-form-input>
                <b-form-input value="" v-else type="password" v-model="password"  id="inline-form-input-name" class="mb-2 mr-sm-2 mb-sm-0"></b-form-input>
            </b-input-group>

            <b-button variant="outline-info" @click="persist">Войти</b-button>
        </b-form>
    </div>
</template>

<script>
    export default {
    data: {
        username: '',
        password: '',
    },
    data() {        
        return {
        showPassword: false,
        password: '',
        username: ''
        };        
    },
    mounted() {
        if (localStorage.username) {
        this.username = localStorage.username;
        }
        if (localStorage.password) {
        this.password = localStorage.password;
        }
    },
    computed: {
        buttonLabel() {
        return (this.showPassword) ? "Hide" : "Show";
        }
    },
    methods: {
        toggleShow() {
            this.showPassword = !this.showPassword;
        },
        persist() {
            localStorage.username = this.username;
            localStorage.password = this.password;
        }
    }
    };
</script>

<style scoped>
    .b-form__wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 500px;
    }
    .b-form {
        width: 400px;
        height: 300px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        border: 0px solid lightblue;
        padding: 15px;
        box-shadow: 0 .5em 1em -.125em rgba(10,10,10,.1),0 0 0 1px rgba(10,10,10,.02);
    }
</style>