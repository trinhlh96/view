<template>
  <div class="container">
        <div class="card">
            <div class="card-header">
                <h3>Login</h3>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="addItem">
                  <div class="form-group">
                    <label>Username:</label>
                    <input type="text" class="form-control" v-model="item.username"/>
                  </div>
                  <div class="form-group">
                    <label>Password:</label>
                    <input type="text" class="form-control" v-model="item.password"/>
                  </div>

                    <div class="form-group">
                        <input type="submit" class="btn btn-primary" value="Login"/>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  components: {
      name: 'Login'
  },
  data() {
      return {
          item: {}
      }
  },
  methods: {
      addItem() {
           let uri = 'http://localhost:8089/api/v2/login';
            this.axios.post(uri, this.item).then((response) => {
              this.$router.push({name: 'Index'});
            });
        }
    }
}
</script>