<template>
  <header>
    <nav class="navbar">

      <div class="navbar_logo">
        <router-link to="/">PETTALK</router-link>
      </div>

      <ul class="navbar_menu">
        <li><router-link to="/">반려상식</router-link></li>
        <li><router-link to="/">커뮤니티</router-link></li>
        <li><router-link to="/">갤러리</router-link></li>
        <li><router-link to="/">동물병원</router-link></li>
        <li><router-link to="/">스토어</router-link></li>
      </ul>

      <ul class="navbar_gnb">
        <li><router-link to="/login">로그인</router-link></li>
        <li><router-link to="/signup">회원가입</router-link></li>
      </ul>
    </nav>

<!--    <div class="header_wrap">-->

<!--      <h1>-->
<!--        <span class="blind">PETTALK</span>-->
<!--      </h1>-->

<!--      <nav>-->
<!--        <ul class="header_menu">-->
<!--          <li><router-link to="/">반려상식</router-link></li>-->
<!--          <li><router-link to="/">커뮤니티</router-link></li>-->
<!--          <li><router-link to="/">갤러리</router-link></li>-->
<!--          <li><router-link to="/">동물병원</router-link></li>-->
<!--          <li><router-link to="/">스토어</router-link></li>-->
<!--        </ul>-->
<!--      </nav>-->

<!--      <ul class="gnb_Menu">-->
<!--        <li><router-link to="/login">로그인</router-link></li>-->
<!--        <li><router-link to="/">회원가입</router-link></li>-->
<!--      </ul>-->

<!--&lt;!&ndash;      <router-link to="/"><span>메인</span></router-link>&ndash;&gt;-->
<!--&lt;!&ndash;      <router-link to="/about"><span>about</span></router-link>&ndash;&gt;-->
<!--&lt;!&ndash;      <router-link to="/login"><span>로그인</span></router-link>&ndash;&gt;-->

<!--    </div>-->
  </header>
</template>

<script>
export default {
    name : "Navigation"
}
</script>

<style>

</style>
