<template>
  <div>
    <NavBar />
    <div class="container">
      <div class="row">
        <div class="col-md-4 offset-md-4 mt-5">
          <b-card header="Register">
            <form action="#" @submit.prevent="onRegister">
              <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" v-model="user.name" class="form-control" />
              </div>
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" v-model="user.email" class="form-control" />
              </div>
              <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" v-model="user.password" class="form-control" />
              </div>
              <div class="form-group">
                <button class="btn btn-info" type="submit">Register</button>
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
  auth: false,
  data() {
    return {
      user: {}
    }
  },
  methods: {
    onRegister() {
      this.$axios.post('/api/register', this.user)
      .then((res)=>{
        if(res.status==202) {
          alert(res.data.message)
          this.user = {}
        }
      })
    }
  }
}
</script>

<style>

</style>