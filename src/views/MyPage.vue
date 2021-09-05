<template>
    <div class="login_wrap">
        <section class="myPage-form">
            <h1>내 정보</h1>
            <form action="">
                <div class="int-area">
                    <label for="uid">아이디</label>
                    <input
                        type="text"
                        name="uid"
                        id="uid"
                        maxlength="15"
                        minlength="2"
                        v-model="uid"
                        autocomplete="off"
                        required
                    >
                </div>

                <div class="int-area">
                    <label for="pw">비밀번호</label>
                    <input
                        type="password"
                        autocomplete="off"
                        required
                        minlength="8"
                        name="pw"
                        id="pw"
                        v-model="password"
                    >
                <div class="myPage_btn">
                    <button @click="onclickMyPage()">수정</button>
                </div>
                </div>


                <div class="int-area">
                    <label for="nickname">닉네임</label>
                    <input
                            type="text"
                            name="nickname"
                            id="nickname"
                            maxlength="15"
                            minlength="2"
                            v-model="nickname"
                            autocomplete="off"
                            required
                    >
                <div class="myPage_btn">
                    <button @click="onclickMyPage()">수정</button>
                </div>
                </div>

                <div class="int-area">
                    <label for="email">이메일</label>
                    <input
                            type="text"
                            name="email"
                            id="email"
                            maxlength="15"
                            minlength="2"
                            v-model="email"
                            autocomplete="off"
                            required
                    >
                <div class="myPage_btn">
                    <button @click="onclickMyPage()">수정</button>
                </div>
                </div>

            </form>
        </section>
    </div>


</template>

<script>
  export default {
    name: 'MyPage',
    data() {
      return {
        uid: '',
        password: '',
        nickname: '',
        email: '',
      }
    },
    methods: {
      async onclickMyPage() {
        await this.$store.dispatch("mypage", {
          userId: this.uid,
          password: this.password,
          nickname: this.nickname,
          email: this.email,
        })
      }
    }
  };
</script>

<style scoped>

.myPage-form > h1 {
    font-size: 33px;
    color: rgb(229, 119, 175);
    font-family: 'Gowun Dodum', sans-serif;
    font-weight: bold;
}

.int-area {
    margin-top: 25px;
}
.int-area > label {
    font-weight: bold;
    font-family: 'Gowun Dodum', sans-serif;
    font-size: 17px;
}

.myPage_btn button {
    border: 1px solid #333;
    padding: 3px 5px;
}



</style>
