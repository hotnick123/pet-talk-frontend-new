<template>
	<div>
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

</style>
