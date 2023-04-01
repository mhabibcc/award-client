<template>
  <div class="login-form container py-4 px-3 mx-auto">
    <form>
      <div class="avatar"></div>
      <h6 class="h6 text-center">Enter your email address to sign in and continue</h6>
      <div class="form-group">
        <input v-model="email" type="email" class="form-control" :class="valid" placeholder="Email Address" required="required">
        <div class="invalid-feedback">
          {{ message }}
        </div>
      </div>
      <div class="d-grid gap-2">
        <input type="button" @click="login()" class="btn btn-primary btn-lg" value="Sign In">
      </div>
    </form>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      email: "",
      valid: "",
      message: "",
      info: null,
	  serverHost: import.meta.env.VITE_SERVER_HOST,
    }
  },
  methods: {
    login() {
		const json = JSON.stringify({ email: this.email });
		console.log(json)
		const url = this.serverHost+'auth/login'
      axios
      .post(url,{email: this.email})
      .then(response => {
		this.info = response.data
		console.log(response.data.status)

		this.$router.push({path: 'feed'})
		this.valid=''
	  }).catch(err => {
		console.log(err.response.status)
		if (err.response.status == 401) {
			this.valid='is-invalid'
			this.message='Email Address is not exists'
		}
	  })
    }
  }

}
</script>
<style scoped>
.form-control {
	box-shadow: none;
	border-color: #ddd;
}
.form-control:focus {
	border-color: #4aba70; 
}
.login-form {
  max-width: 350px;
	/* width: 350px; */
	/* margin: 0 auto; */
	/* padding: 30px 0; */
}
.login-form form {
	color: #434343;
	border-radius: 1px;
	margin-bottom: 15px;
	background: #fff;
	border: 1px solid #f3f3f3;
	box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
	padding: 30px;
}
.login-form h4 {
	text-align: center;
	font-size: 22px;
	margin-bottom: 20px;
}
.login-form .avatar {
	color: #fff;
	margin: 0 auto 10px;
	text-align: center;
	width: 200px;
	height: 200px;
	/* border-radius: 50%; */
	z-index: 9;
	/* background: #4aba70; */
  background-image: url('/award-logo.png');
  background-size: contain;
	padding: 15px;
	/* box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.1); */
}
.login-form .avatar i {
	font-size: 62px;
}
.login-form .form-group {
	margin-bottom: 20px;
}
.login-form .form-control, .login-form .btn {
	min-height: 40px;
	border-radius: 2px; 
	transition: all 0.5s;
}
.login-form .close {
	position: absolute;
	top: 15px;
	right: 15px;
}
.login-form .btn, .login-form .btn:active {
	background: #4aba70 !important;
	border: none;
	line-height: normal;
}
.login-form .btn:hover, .login-form .btn:focus {
	background: #42ae68 !important;
}
.login-form .checkbox-inline {
	float: left;
}
.login-form input[type="checkbox"] {
	position: relative;
	top: 2px;
}
.login-form .forgot-link {
	float: right;
}
.login-form .small {
	font-size: 13px;
}
.login-form a {
	color: #4aba70;
}
</style>