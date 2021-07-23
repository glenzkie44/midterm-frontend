<template>
  <div>
    <NavBar />
    <div class="container">
      <div class="row">
        <div class="col-md-4 offset-md-4 mt-5">
          <b-card header="Login">
            <form action="#" @submit.prevent="onLogin()">
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" v-model="creds.email" class="form-control" />
              </div>
              <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" v-model="creds.password" class="form-control" />
              </div>
              <div class="form-group">
                <button class="btn btn-info" type="submit">Login</button>
              </div>
            </form>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      creds: {}
    }
  },
  methods: {
    async onLogin() {
      await this.$auth.loginWith('local', {data: this.creds})
      .then(() => {
      })
      .catch((err)=>{
        alert("Invalid creds")
      })
    }
  }
}
</script>

<style>

</style>