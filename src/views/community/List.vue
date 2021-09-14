<template>

	<div class="board_wrap">
		<h1>커뮤니티</h1>
		<b-table

						striped
						hover
						:items="boardList"
						:per-page="perPage"
						:current-page="currentPage"
						:fields="fields"
						@row-clicked="rowClick"
		></b-table>
		<!--		<div class="text-center">-->
		<!--			<v-container>-->
		<!--				<v-row justify="center">-->
		<!--					<v-col cols="12">-->
		<!--						<v-container class="max-width">-->
		<!--							<v-pagination-->
		<!--											v-model="currentPage"-->
		<!--											class="my-4"-->
		<!--											:length="totalPage"-->
		<!--											:value="currentPage"-->
		<!--							></v-pagination>-->
		<!--						</v-container>-->
		<!--					</v-col>-->
		<!--				</v-row>-->
		<!--			</v-container>-->
		<!--		</div>-->
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
	.board_wrap {
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

	table {
		margin-top: 50px;
		--bs-table-striped-bg: none;
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
