<template>
	<footer id="footer">
		<div class="inner">
			<div class="fl">
				<ul>
					<li><a href="">이용약관</a></li>
					<li><a href="">개인정보취급방침</a></li>
					<li><a href="">매장안내</a></li>
					<li><a href="">고객센터</a></li>
				</ul>

				<p>
					(주)PETTALK / 대표이사 : 최혜주 / 경기도 성남시 분당구 북정로 6(정자동 178-1)<br />
					대표메일주소 : 6547123@naver.com / TEL : 010-9401-5955<br />
					사업자등록번호 : 123-45-67890
				</p>
				<div class="copyRight">Copyright ⓒ 2021 CHOI HYE JOO. All right reserved.</div>
			</div>
			<div class="fr">
				<div class="customer">
					<P><em>고객센터 010-9401-5955</em></P>
					<P>월-금 : 오전 10시 ~ 오후 5시 (휴게시간 12:30 ~ 2:00)<br />토,일,공휴일 휴무</P>
				</div>
				<ul class="sns">
					<li><a href=""><i class="fab fa-facebook-square"></i></a></li>
					<li><a href=""><i class="fab fa-youtube"></i></a></li>
					<li><a href=""><i class="fab fa-twitter"></i></a></li>

					<li>
						<router-link to=""><v-icon>mdi-facebook</v-icon></router-link>
					</li>
					<li>
						<router-link to=""><v-icon>mdi-youtube</v-icon></router-link>
					</li>
					<li>
						<router-link to=""><v-icon>mdi-twitter</v-icon></router-link>
					</li>

				</ul>
			</div>
		</div>
	</footer>
</template>

<script>
  export default {
    name: "Footer"
  }
</script>

<style scoped>
	#footer {
		background: #fff;
		margin-top: 300px;
		position: relative;
		transition: 0.5s;
		border-top: 1px dashed #ddd;
		padding: 50px 100px;
	}

	#footer:after {
		content: "";
		display: block;
		clear: both;
	}

	#footer .inner {
		width: 1180px;
		margin: 0 auto;
		position: relative;
	}

	#footer .inner .fl {
		float: left;
	}


	#footer .inner .fl ul::after {
		content: '';
		clear: both;
		display: block;
	}

	#footer .inner .fl ul li {
		float: left;

	}

	#footer .inner .fl ul li:not(:last-of-type) {
		margin-right: 40px; }

	#footer .inner .fl ul li a {
		font-size: 13px;
		border-bottom: 1px solid #666;
		color: #111;
	}

	#footer .inner .fl p {
		line-height: 25px;
		font-size: 13px;
		margin: 22px 0;
	}

	#footer .inner .fl .copyRight {
		font-size: 13px;
	}

	#footer .inner .fr {
		float: right;
	}

	#footer .inner .fr p {
		font-size: 13px;
		line-height: 25px;
	}

	#footer .inner .fr p em {
		font-size: 20px;
		font-style: normal;
		font-weight: 600;
	}

	#footer .inner .fr .sns {
		margin-top: 30px;
	}

	#footer .inner .fr .sns li {
		float: left;

	}

	#footer .inner .fr .sns li:not(:last-of-type) {
		margin-right: 30px;
	}

	#footer .inner .fr .sns li i {
		font-size: 45px;
	}
</style>
