<template>
  <div style="background: #3490dc;">
    <div class="container">
      <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <a class="navbar-brand" href="#">Mini-CRM</a>
        <button 
          class="navbar-toggler" 
          type="button" 
          data-toggle="collapse" 
          data-target="#navbarSupportedContent" 
          >
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item">
              <router-link to="/" class="nav-link">Home </router-link>
            </li>
          </ul>

          <ul class="navbar-nav ml-auto">
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                {{ app.user ? app.user.name : 'Account' }}
              </a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <div v-if="!app.user">
                  <router-link to="/login" class="dropdown-item">Login</router-link>
                  <router-link to="/register" class="dropdown-item">register</router-link>
                </div>

                <a v-else @click="logout" href="javascript:;" class="dropdown-item">Logout</a>

              </div>
            </li>

          </ul>
          
        </div>
      </nav>




      
    </div>
  </div>
</template>
 

 <script>
 export default {
   name: 'navbar',
   props: ['app'],
   data(){
      return {};
    },
    methods: { 
      logout()
      {
        this.app.req.post('auth/logout').then(() => {
          this.app.user = null;
          this.$router.push('/login');
        });
      }
    } 
 };
 </script>

 <style>
 </style>

