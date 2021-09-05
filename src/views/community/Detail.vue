<template>
	<div>
		<h1>커뮤니티</h1>
		<b-card>
			<div class="content-detail-content-info">
				<div class="content-detail-content-info-left">
					<div class="content-detail-content-info-left-number">{{id}}</div>
					<div class="content-detail-content-info-left-subject">{{this.detail.title}}</div>
				</div>
				<div class="content-detail-content-info-right">
					<div class="content-detail-content-info-right-user">글쓴이: {{this.detail.writer}}</div>
					<div class="content-detail-content-info-right-created">등록일: {{this.detail.createdAt}}</div>
				</div>
			</div>
			<div class="content-detail-content">{{this.detail.content}}</div>
			<div class="content-detail-button">
				<b-button variant="primary" @click="onClickModifyBtn">수정</b-button>&nbsp;
				<b-button variant="warning" @click="onClickDeleteBtn">삭제</b-button>
				<b-button variant="secondary" @click="onClickListBtn">목록</b-button>
			</div>
			<div class="content-detail-comment">
				<CommentList :contentId="contentId"></CommentList>
			</div>
		</b-card>
	</div>
</template>

<script>
  import axios from "axios";

  export default {
    name: "BoardDetail",
    mounted() {
      axios.get(`http://localhost:8081/board/${this.id}`)
        .then((res) => {
          this.detail.title = res.data.data.title;
          this.detail.content = res.data.data.content;
          this.detail.writer = res.data.data.writer;
          this.detail.createdAt = res.data.data.createdAt;
        })
        .catch((err) => {
          console.log(err);
          alert("게시글 조회 오류");
        })
    },
    data() {
      return {
        id: this.$route.params.id,
        detail: {
          title: '',
          content: '',
          writer: '',
          createdAt: '',
        },
      };
    },
    methods: {
      onClickModifyBtn() {
        this.$router.push({name: "BoardModify", params: {id: this.id}});
      },
      onClickDeleteBtn() {
        if (confirm("삭제하시겠습니까?")) {
          axios.post(`http://localhost:8081/board/delete/${this.id}`)
            .then((res) => {
              if (res.data.data === true) {
                alert('글 삭제 성공');
                this.$router.push({name: "BoardList"});
              } else {
                alert('글 삭제 실패');
              }
            })
            .catch((err) => {
              console.log(err);
              alert("알 수 없는 오류 발생");
            })
        }
      },
      onClickListBtn() {
        this.$router.push({name: "BoardList"});
      }
    },
    components: {}
  };
</script>
<style scoped>
	.content-detail-content-info {
		border: 1px solid black;
		display: flex;
		justify-content: space-between;
	}

	.content-detail-content-info-left {
		width: 720px;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
	}

	.content-detail-content-info-right {
		width: 300px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 1rem;
	}

	.content-detail-content {
		border: 1px solid black;
		margin-top: 1rem;
		padding-top: 1rem;
		min-height: 720px;
	}

	.content-detail-button {
		border: 1px solid black;
		margin-top: 1rem;
		padding: 2rem;
	}

	.content-detail-comment {
		border: 1px solid black;
		margin-top: 1rem;
		padding: 2rem;
	}

	.page {
		width: 1200px;
		margin-top: 100px;

		font-family: 'Gowun Dodum', sans-serif;
	}

	h1 {
		font-size: 33px;
		font-weight: bold;
		width: 100%;
		color: rgb(229, 119, 175);
	}
</style>
