<template>
    <div class="wrap">
    <section class="login-form">
        <h1>PETTALK</h1>


            <div class="int-area">
                <input type="text" placeholder="아이디" autocomplete="off" required v-model="uid">
<!--                <lable for="id"></lable>-->
            </div>

            <div class="int-area">
                <input type="password" placeholder="비밀번호" autocomplete="off" required v-model="password">
<!--                <lable for="pw"></lable>-->
            </div>

            <div class="btn-area">
                <button @click="onClickLogin">로그인</button>
            </div>


        <div class="caption">
            <router-link to="/signup">회원가입</router-link>
            <router-link to="/">비밀번호 찾기</router-link>
        </div>
    </section>
    </div>

<!--    <div>-->
<!--        <div class="login-wrap">-->
<!--            <div class="input-area">-->
<!--                <select-form/>-->
<!--                <input type="text" placeholder="아이디"/>-->
<!--                <input type="password" placeholder="비밀번호"/>-->
<!--                <div class="com-check">-->
<!--                    <input type="checkbox" name="check-all" id="check-all">-->
<!--                    <label for="check-all">아이디 저장</label>-->
<!--                </div>-->
<!--            </div>-->
<!--            <div class="btn-area">-->
<!--                <button class="com-btn">로그인</button>-->
<!--            </div>-->
<!--        </div>-->
<!--    </div>-->
</template>

<script>
export default {
    name: 'Login',
    data: () => ({
    uid: '',
    password: ''
}),
  methods: {
    onClickLogin () {
      console.log(this.uid)
      console.log(this.password)
    }
  }
}
</script>

<style scoped>

</style>
