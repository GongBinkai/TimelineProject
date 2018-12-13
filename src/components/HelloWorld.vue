<template>
  <div class="hello">
    <button @click="register">注册</button>
    <button @click="login">登录</button>
    <button @click="release">发布</button>
  </div>
</template>

<script>
	var token;
export default {
  data () {
  	return {}
  },
  methods: {
  	/*
	  	register() {
	  		
					this.$axios.post('/api/users/login', {
					"user": {
						//"username" : "gbk",
						"email": "gbk@gmail.com",
						"password": "gbk"
						//"image": "image"
					}
				}).then(response => {
					console.log(response.data.user.token);
					//token = response.data.user.token
					//.$cookieStore.setCookie("token", response.data.user.token);
					//console.log(token);
				})
		}
		*/
		register() {
				this.$axios({
					url: '/api/users',
					method: 'post',
					data: {
    					"user":{
    							"username": "zxl2222",
    							"email": "zxl22222@zxl.cn",
    							"password": "zxl2222"
 						 }
					}
				}).then(function(response) {
					console.log(response);
				})
			},
			login() {
				this.$axios({
					url: '/api/users/login',
					method: 'post',
					data: {
						"user": {
							"email": "zxl22@zxl.cn",
							"password": "zxl22"
						}
					}
				}).then(function(response) {
					console.log(response);
					token = response.data.user.token;
					console.log(token);
				})
								
			},
			release() {
				this.$axios({
					url: '/api/messages',
					method: 'post',
					headers : {
						"Authorization" : 'Bearer ' + token
					},
					data: {
						"message": {
							"body": "You are fat, too."
						}
					}
				}).then(function(response) {
					console.log(response);
				})
			}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
