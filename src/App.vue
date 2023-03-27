<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="info">

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/">Главная</b-nav-item>          
          <b-nav-item to="/profile">Профиль</b-nav-item>
          <b-nav-item to="/ticket">Список обращений</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown class="show__logout" right>
            <!-- Using 'button-content' slot -->
            <template #button-content>
              <em>Пользователь</em>
            </template>
            <b-dropdown-item @click="logout">Выйти</b-dropdown-item>
          </b-nav-item-dropdown>
          <!-- <b-nav-item-dropdown v-if="isLoggedIn" class="show__logout" right>
            <template #button-content>
              <em>Пользователь</em>
            </template>
            <b-dropdown-item @click="logout">Выйти</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item-dropdown v-else class="hide__logout" right>
            <template #button-content>
              <em>Пользователь</em>
            </template>
            <b-dropdown-item @click="logout">Выйти</b-dropdown-item>
          </b-nav-item-dropdown> -->
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <router-view/>
  </div>
</template>


<script>
  export default {
    beforeCreate() {
      localStorage.username = '';
      localStorage.password = '';
    },
    computed : {
      isLoggedIn : function(){
        if (localStorage.username!='' && localStorage.password!='') {
          this.username = localStorage.username;
          return true
        }        
      }
    },
    methods: {
      logout: function () {
        localStorage.username = '';
        localStorage.password = '';
      }
    },
  }
</script>

<style>
body {
  width: 100vw;
  height: 100vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  text-decoration: none;
}
.show__logout {
  display: block;
}
.hide__logout {
  display: none;
}
</style>
