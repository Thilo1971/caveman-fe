<template>
  <div >    
    <b-sidebar id="menu-sidebar" title="Menu" shadow no-header>
        <b-button v-b-toggle.menu-sidebar class='menu-button' ><b-icon-chevron-bar-left></b-icon-chevron-bar-left></b-button>
      <h1>Menu</h1>
        <b-nav vertical tabs>
            <router-link tag='b-nav-item' to="/dashboard">Dashboard</router-link>
            <router-link tag='b-nav-item' to="/profile">My Profile</router-link>    
            <router-link tag='b-nav-item' to="/caves">Caves</router-link>
            <a tag='b-nav-item' @click="logout">Logout</a>
            <!-- <b-nav-item-dropdown text="Admin" block menu-class="w-100">
                <b-dropdown-item>Manage Users</b-dropdown-item>
                <b-dropdown-item>Manage Caveman</b-dropdown-item>
            </b-nav-item-dropdown> -->
        </b-nav>
    </b-sidebar>
  </div>
</template>

<script>
    import { mapActions } from "vuex";
    export default {    
       name: 'Sidebar',
       methods: {
            ...mapActions(["LogOut"]),
            async logout() {
                try{
                    await this.LogOut();
                } catch (e) {
                    console.log(e)
                }
                this.$router.push({ name: 'login'});
            }
        },
    }
</script>

<style>
    .menu-button {        
        margin-left: 8px;
        margin-top: 8px;
        float: left;
    }
</style>
