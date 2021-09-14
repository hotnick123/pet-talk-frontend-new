<template>
	<div class="home_wrap">
		<swiper class="swiper" :options="swiperOption">
			<swiper-slide><img src="../assets/img/Banner3.png"></swiper-slide>
			<swiper-slide><img src="../assets/img/Banner4.png"></swiper-slide>
			<swiper-slide><img src="../assets/img/Banner6.png"></swiper-slide>
			<swiper-slide><img src="../assets/img/Banner1.png"></swiper-slide>
			<swiper-slide><img src="../assets/img/Banner2.png"></swiper-slide>
			<div class="swiper-pagination" slot="pagination"></div>
			<div class="swiper-button-prev" slot="button-prev"></div>
			<div class="swiper-button-next" slot="button-next"></div>
		</swiper>


		<div class="comm_ranking">
			<h1>인기 게시글</h1>
			<ul>
				<li>1. 리스트항목</li>
				<li>2. 리스트항목</li>
				<li>3. 리스트항목</li>
				<li>4. 리스트항목</li>
				<li>5. 리스트항목</li>
				<li>6. 리스트항목</li>
				<li>7. 리스트항목</li>
				<li>8. 리스트항목</li>
				<li>9. 리스트항목</li>
				<li>10. 리스트항목</li>
			</ul>
		</div>

		<section id="icon_wrap">
			<div class="inner">
				<h1>Lorem, ipsum dolor.</h1>

				<div class="icon">
					<article>
						<div class="pic">
							<v-icon>mdi-paw</v-icon>
							<p>icon</p>
						</div>
					</article>
					<article>
						<div class="pic">
							<v-icon>mdi-cat</v-icon>
							<p>icon</p>
						</div>
					</article>
					<article>
						<div class="pic">
							<v-icon>mdi-dog</v-icon>
							<p>icon</p>
						</div>
					</article>
					<article>
						<div class="pic">
							<v-icon>mdi-hospital-box</v-icon>
							<p>icon</p>
						</div>
					</article>
					<article>
						<div class="pic">
							<v-icon>mdi-creation</v-icon>
							<p>icon</p>
						</div>
					</article>
					<article>
						<div class="pic">
							<v-icon>mdi-lightbulb-on</v-icon>
							<p>icon</p>
						</div>
					</article>

				</div>
			</div>
		</section>
	</div>

</template>

<script>
  import {Swiper, SwiperSlide} from 'vue-awesome-swiper'
  import 'swiper/css/swiper.css'

  export default {
    name: 'swiper-example-loop',
    title: 'Loop mode / Infinite loop',
    components: {Swiper, SwiperSlide},
    data() {
      return {
        swiperOption: {
          slidesPerView: 1,
          spaceBetween: 30,
          loop: true,
          pagination: {el: '.swiper-pagination', clickable: true},
          navigation: {nextEl: '.swiper-button-next', prevEl: '.swiper-button-prev'},
          autoplay: {delay: 2500, disableOnInteraction: false}
        }
      }
    }
  }

</script>

<style scoped>
	.home_wrap {
		width: 1200px;
		font-family: 'Gowun Dodum', sans-serif;
	}

	.swiper {
		height: auto;
		width: 1200px;
		margin-top: 10px;
	}

	swiper-slide {
		display: flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		font-weight: bold;
	}

	.swiper-slide img {
		width: 100%;
	}

	h1 {
		font-size: 33px;
		font-weight: bold;

		color: rgb(229, 119, 175);

	}

	/* 아이콘 */
	#icon_wrap {
		width: 100%;
		/*padding: 50px 40px;*/
		box-sizing: border-box;
		transition: 0.5s;
		background-color: rgb(252, 228, 240);
	}

	#icon_wrap .inner {
		width: 1180px;
		margin: 0 auto;
	}

	#icon_wrap .inner h1 {
		float: left;
	}

	#icon_wrap .inner .icon {
		float: right;
		transition: 0.5s;
		box-sizing: border-box;
	}

	#icon_wrap .inner .icon article {
		float: left;
		margin-left: 65px;
		width: 58px;
	}

	#icon_wrap .inner .icon article:nth-of-type(1) {
		margin-left: 0px;
		/*border: 1px solid red;*/
	}

	#icon_wrap .inner .icon article .pic {
		width: 100%;
		height: 58px;
		text-align: center;
	}

	#icon_wrap .inner .icon article .pic > i {
		font-size: 40px;
		color: #777;
		transition: .3s;
	}

	#icon_wrap .inner .icon article .pic > p {
		font-size: 11px;
		margin-top: 10px;
	}

	#icon_wrap .inner .icon article .pic:hover i {
		transform: scale(1.2);
	}
</style>
