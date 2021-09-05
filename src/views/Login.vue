

<template>
    <div class="login_wrap">
    <section class="login-form">
        <h1>PETTALK</h1>

            <div class="int-area id_input">
                <input type="text" placeholder="아이디" autocomplete="off" required v-model="uid">
            </div>

            <div class="int-area pw_input">
                <input type="password" placeholder="비밀번호" autocomplete="off" required v-model="password">
            </div>

            <div class="btn-area">
                <button @click="onClickLogin()">로그인</button>
            </div>


        <div class="caption">
            <router-link to="/signup">회원가입</router-link>
            <router-link to="/">비밀번호 찾기</router-link>
        </div>

    </section>
    </div>


</template>

<script>
// import { mapActions } from "vuex";

export default {
    name: 'Login',
    data() {
      return {
        uid: '',
        password: '',
      }
    },
  // computed: {
  //     ...mapState(["isLogin", "isLoginError"])
  // },
  methods: {
    // ...mapActions(["login"]),
    onClickLogin() {
        this.$store.dispatch("login", {
          loginId: this.uid,
          password: this.password,
        })
        this.$router.push({name: "Home"});
    }
  }
}
</script>

<style scoped>




</style>
