<template>
  <b-container>
    <b-row align-h="center" class="mt-5 mb-5">
      <b-col cols="5">
        <b-card class="p-3">
          <h3 class="mb-4">Login</h3>
          <b-form @submit.prevent="onSubmit" @reset="onReset">
            <b-form-group
              id="input-group-1"
              label="Email address:"
              label-for="input-1"
            >
              <b-form-input
                id="input-1"
                v-model="form.email"
                type="email"
                required
                placeholder="Enter email"
              ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-2" label="Password:" label-for="input-2">
              <b-form-input
                id="input-2"
                v-model="form.password"
                type="password"
                required
                placeholder="Password"
              ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-4">
              <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
                <b-form-checkbox value="remember">Remember me</b-form-checkbox>
              </b-form-checkbox-group>
            </b-form-group>

            <div class="d-flex justify-content-between">
              <div>
                <b-button type="submit" variant="primary">Submit</b-button>&nbsp;
                <b-button type="reset" variant="danger">Reset</b-button>
              </div>
              <div>
                <a href="#">Forgot password</a>
              </div>
            </div>
            
          </b-form>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data: () => ({
      form: {
        email: '',
        password: '',
        checked: []
      }
    }),
    methods: {
      onSubmit() {
        console.log(this.form)
        if (this.form.checked.length) {
          localStorage.setItem(this.form.email, this.form.password)
        }
        this.form = {}
      },
      onReset() {
        this.form.email = ''
        this.form.name = ''
        this.form.checked = []
      }
    }
}
</script>

<style>
  body {
    background-color: #eef1f4;
    min-height: 100vh;
  }
</style>