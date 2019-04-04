<template>
  <div>
    <h4>Register</h4>
    <form @submit.prevent="register">
      <label for="username">Name</label>
      <div>
          <input id="username" type="text" v-model="username" required autofocus>
      </div>

      <label for="email" >E-Mail Address</label>
      <div>
          <input id="email" type="email" v-model="email" required>
      </div>

      <label for="password1">Password</label>
      <div>
          <input id="password1" type="password" v-model="password1" required>
      </div>

      <label for="password2">Confirm Password</label>
      <div>
          <input id="password2" type="password" v-model="password2" required>
      </div>

      <div>
          <button type="submit">Register</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      email: "",
      password1: "",
      password2: "",
    };
  },

  methods: {
    register: function() {
      let form = new FormData();
          form.append('username', this.username);
          form.append('email', this.email);
          form.append('password1', this.password);
          form.append('password2', this.password);
      this.$store
        .dispatch("register", form)
        .then(() => this.$router.push("/"))
        .catch(err => console.log(err));
    }
  }
};
</script>