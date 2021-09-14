<template>

	<div class="gallery_wrap">
		<h1>갤러리</h1>
		<v-row>
			<v-col
							v-for="n in 3"
							:key="n"
							cols="12"
							sm="4"
			>
				<v-card
								class="mx-auto"
								max-width="390"
				>
					<v-img
									src="../../assets/img/gallery1.jpg"
									height="250"
					></v-img>

					<v-card-title>
						우리집 사탄
					</v-card-title>

					<v-card-subtitle>
						글 내용 --- - -- - - --
					</v-card-subtitle>

					<v-list-item>
						<v-list-item-subtitle>
							<strong>닉네임1</strong> <span>2021-09-14</span> <em>조회 10</em>
						</v-list-item-subtitle>

					</v-list-item>

				</v-card>

				<v-card
								class="mx-auto"
								max-width="390"
				>
					<v-img
									src="../../assets/img/gallery2.jpg"
									height="250"
					></v-img>

					<v-card-title>
						저 어때용?
					</v-card-title>

					<v-card-subtitle>
						글 내용 --- - -- - - --
					</v-card-subtitle>

					<v-list-item>
						<v-list-item-subtitle>
							<strong>닉네임1</strong> <span>2021-09-14</span> <em>조회 10</em>
						</v-list-item-subtitle>

					</v-list-item>

				</v-card>

			</v-col>
		</v-row>



		<div class="btn_wrap">
			<b-button @click="onClickWriteBtn">글쓰기</b-button>
		</div>
		<b-pagination aria-controls="my-table" align="center" first-class="first" prev-class="prev" next-class="next"
      last-class="last"
      v-model="currentPage" :total-rows="totalItems" :per-page="perPage"
      @change="handlerPagenation">
		</b-pagination>


	</div>

</template>

<script>
  import api from "../../api/api";
  import dayjs from "dayjs";

  export default {
    name: 'BoardList',
    async mounted() {
      await this.fetchBoardList();
    },
    data() {
      return {
        currentPage: 1, // 현재 페이지
        perPage: 10, // 페이지당 보여줄 갯수
        totalPage: '',
        totalItems: '',
        // bootstrap 'b-table' 필드 설정
        fields: [
          {
            key: "id",
            label: "번호"
          },
          {
            key: "title",
            label: "제목"
          },
          {
            key: "writerName",
            label: "작성자"
          },
          {
            key: "createdAt",
            label: "등록일",

          },
          {
            key: "count",
            label: "조회",
          },
        ],
        boardList: [],
        // items: items
      };
    },
    methods: {
      async fetchBoardList() {
        return await api.get(`/board/list/${this.currentPage}/${this.perPage}`)
          .then((res) => {
            this.boardList = res.data.data.content;
            this.boardList.map((v) => {
              v.createdAt = dayjs(v.createdAt).format("YYYY-MM-DD HH:mm");
            })
            this.totalPage = res.data.data.totalPages;
            this.totalItems = res.data.data.totalElements;
            console.log(this.boardList);
          }).catch((err) => {
            console.log(err);
            alert("게시글 목록 조회 오류");
          });
      },
      rowClick(item) {
        this.$router.push({
          path: `/community/detail/${item.id}`
        });
      },
      onClickWriteBtn() {
        this.$router.push({name: 'BoardCreate'});
      },
      handlerPagenation(v) {
        this.currentPage = v;
        this.fetchBoardList();
      }
    },
    computed: {
      rows() {
        return this.items.length;
      }
    },
  }
</script>

<style scoped>
	em {
		font-style: normal;
	}

	.gallery_wrap {
		width: 1200px;
		height: 100vh;
		display: flex;
		flex-direction: column;
		/*justify-content: space-evenly;*/
		align-items: center;
		margin-top: 100px;

		font-family: 'Gowun Dodum', sans-serif;
	}

	h1 {
		font-size: 33px;
		font-weight: bold;
		width: 100%;
		color: rgb(229, 119, 175);
	}

	.v-card {
		margin-bottom: 20px;
	}

	.btn_wrap {
		width: 100%;
	}

	.btn {
		width: 90px;
		height: 35px;
		color: #fff;
		background-color: rgb(236, 152, 195);
		border: none;
		border-radius: 5px;
		font-size: 18px;
		line-height: 18px;
		float: right;
		font-family: 'Gowun Dodum', sans-serif;
	}

	.pagination {
		margin-top: 50px;
	}

</style>
