<template>
    <div id="login">
        <h1>Login</h1>
        <form>
            <input
                type="text"
                name="username"
                id="username"
                placeholder="Username"
                v-model="input_user"
            />
            <input
                type="text"
                name="password"
                id="password"
                placeholder="Password"
                v-model="input_pass"
            />
            <br />
            <button>Login</button>
        </form>
        <!-- <router-link class="link" to="/forgot">Forgot password?</router-link>
        <router-link to="/signup">Sign up</router-link> -->

        <!-- Check that the SDK client is not currently loading before accessing is methods -->
        <div v-if="!$auth.loading">
            <!-- show login when not authenticated -->
            <a
                v-if="!$auth.isAuthenticated"
                @click="login"
                class="button is-dark"
                ><strong>Sign in</strong></a
            >
            <!-- show logout when authenticated -->
            <a
                v-if="$auth.isAuthenticated"
                @click="logout"
                class="button is-dark"
                ><strong>Log out</strong></a
            >
        </div>
    </div>
</template>

<script>
export default {
    name: "Login",
    props: {
        isLoggedIn: Boolean,
    },
    data() {
        return {
            input_user: "",
            input_pass: "",
        };
    },
    methods: {
        // Log the user in
        login() {
            this.$auth.loginWithRedirect();
        },
        // Log the user out
        logout() {
            this.$auth.logout({
                returnTo: window.location.origin,
            });
        },
    },
};
</script>

<style scoped>
#login {
    align-items: center;
    background-color: #42b983;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    padding-bottom: 50px;
}
form {
    display: flex;
    flex-direction: column;
}
button {
    border-radius: 15px;
    margin: 5px;
    padding: 5px;
    background: white;
    border: 1px solid;
    width: 250px;
}
input {
    margin: 5px;
}
</style>
