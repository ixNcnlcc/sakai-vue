<script>
export default {
    data() {
        return {
            student: {
                name: '',
                password: ''
            }
        };
    }
};
</script>

<template>
    <form>
        <div>
            <header>Login</header>
        </div>

        <div class="form-control">
            <label for="name">Username</label>
            <input type="text" placeholder="Username" v-model="student.name" />
        </div>

        <div class="form-control">
            <label for="password">Password</label>
            <input type="text" placeholder="Password" v-model="student.password" />
        </div>

        <div>
            <div>
                <input type="checkbox" value="remember me" />
                <label for="remember me">Remember me</label>
            </div>
            <div>
                <a href="">Forgot password?</a>
            </div>
        </div>

        <div>
            <div>
                <button class="login">Log In</button>
            </div>
            <div>
                <button class="register">Register</button>
            </div>
        </div>

        <div>
            <button class="google">Google Log In</button>
        </div>
    </form>
</template>

<style scoped>
header {
    font: sans-serif;
    font-size: 40px;
    text-align: center;
}

form {
    margin: 2rem auto;
    max-width: 40rem;
    border-radius: 12px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
    padding: 2rem;
    background: #fff;
}

.form-control {
    margin: 0.5rem 0;
}

label {
    font-weight: bold;
    font-family: sans-serif;
}

input {
    display: block;
    width: 100%;
    font-family: sans-serif;
    margin-top: 0.5rem;
}

.login {
    background: #056fe9;
    font-family: sans-serif;
    font-weight: bold;
    font-size: 14px;
    color: white;
    width: 100%;
    cursor: pointer;
    padding: 7px 10.5px;
    border-radius: 5px;
    border: 1px;
}

.google {
    background: #056fe9;
    margin: 0.5rem auto;
    font: sans-serif;
    font-size: 14px;
    color: white;
    width: 100%;
    cursor: pointer;
    padding: 7px 10.5px;
    border-radius: 5px;
    border: 1px;
}
</style>
