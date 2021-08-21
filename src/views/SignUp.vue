<template>
    <div class="signup_wrap">
        <section class="signup-form">
            <h1>회원가입</h1>
            <form action="">

                <div class="int-area">
                    <label class="email_label" for="email">이메일</label>

                    <div class="email_input">
                        <span class="email_lacal">
                            <input type="text" placeholder="이메일" name="email" id="email">
                        </span>
                        <span class="email_separator">@</span>
                        <span class="email_domain">
                            <select class="form-control empty">
                                <option value="" disabled="">선택해주세요</option>
                                <option value="naver.com">naver.com</option>
                                <option value="hanmail.net">hanmail.net</option>
                                <option value="daum.net">daum.net</option>
                                <option value="gmail.com">gmail.com</option>
                                <option value="nate.com">nate.com</option>
                                <option value="hotmail.com">hotmail.com</option>
                                <option value="outlook.com">outlook.com</option>
                                <option value="icloud.com">icloud.com</option>
                                <option value="_manual">직접입력</option>
                            </select>
                        </span>
                    </div>

                </div>

                <div class="email_btn">
                    <button type="button">이메일 인증하기</button>
                </div>

                <div class="int-area">
                    <label for="pw">비밀번호</label>
                    <div class="pw_description">
                        영문, 숫자를 포함한 8자 이상의 비밀번호를 입력해주세요.
                    </div>
                        <input type="password" placeholder="비밀번호" name="pw" id="pw">
                </div>

                <div class="int-area">
                    <label for="confirmPassword">비밀번호 확인</label>
                    <input type="password" placeholder="비밀번호 확인" name="confirmPassword" id="confirmPassword">
                </div>

                <div class="int-area">
                    <label for="nickname">닉네임</label>
                    <div class="nick_description">다른 유저와 겹치지 않는 별명을 입력해주ㅅㅔ요. (2자~15자)</div>
                    <input type="text" name="nickname" id="nickname" placeholder="별명 (2자~15자)">
               </div>

<!--                <div class="int-area">-->
<!--                    <label>약관동의</label>-->
<!--                    -->
<!--                </div>-->
                <button type="submit">회원가입하기</button>


            </form>


        </section>
    </div>
</template>

<script>
  export default {
    name: "SignUp"
  }
</script>

<style scoped>

</style>
