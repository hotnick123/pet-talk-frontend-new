<template>
  <div>
    <h1>커뮤니티</h1>
    <b-card>
      <div class="content-detail-content-info">
        <div class="content-detail-content-info-left">
          <div class="content-detail-content-info-left-number">{{ id }}</div>
          <div class="content-detail-content-info-left-subject">{{ this.board.title }}</div>
        </div>
        <div class="content-detail-content-info-right">
          <div class="content-detail-content-info-right-user">글쓴이: {{ this.board.writerName }}</div>
          <div class="content-detail-content-info-right-created">등록일: {{ this.board.createdAt }}</div>
        </div>
      </div>
      <div class="content-detail-content">{{ this.board.content }}</div>
      <div class="content-detail-button">
        <b-button variant="primary" @click="onClickModifyBtn">수정</b-button>&nbsp;
        <b-button variant="warning" @click="onClickDeleteBtn">삭제</b-button>
        <b-button variant="secondary" @click="onClickListBtn">목록</b-button>
      </div>

      <div class="int-area">
        <input
            type="text"
            placeholder="댓글을 입력해주세요."
            autocomplete="off"
            required
            v-model="commentInput"
        >
        <div class="comment_btn">
          <button @click="onClickCommentBtn">등록</button>
        </div>
      </div>

      <div v-for="(cl, index) in commentList" class="content-detail-comment" :key="index">
        <div>
          <span>{{ cl.writer }}</span>
          <span>{{ cl.content }}</span>
          <span>{{ cl.createdAt }}</span>
        </div>
      </div>
    </b-card>
  </div>
</template>

<script>
import api from "../../api/api";

export default {
  name: "BoardDetail",
  async mounted() {
    await this.fetchBoardDetail();
  },
  data() {
    return {
      userId: this.$store.state.userInfo.id,
      id: this.$route.params.id,
      commentList: [],
      board: {
        id: '',
        title: '',
        content: '',
        writer: '',
        createdAt: '',
        writerName: '',
      },
      commentInput: '',
    };
  },
  methods: {
    async fetchBoardDetail() {
      await api.get(`/board/${this.id}`)
          .then((res) => {
            console.log(res);
            this.board.title = res.data.data.board.title;
            this.board.content = res.data.data.board.content;
            this.board.writer = res.data.data.board.writer;
            this.board.writerName = res.data.data.board.writerName;
            this.board.createdAt = res.data.data.board.createdAt;
            this.commentList = res.data.data.comment ? res.data.data.comment : [];
          })
          .catch((err) => {
            console.log(err);
            alert("게시글 조회 오류");
          })
    },
    onClickModifyBtn() {
      this.$router.push({name: "BoardModify", params: {id: this.id}});
    },
    onClickDeleteBtn() {
      if (confirm("삭제하시겠습니까?")) {
        api.post(`/board/delete/${this.id}`)
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
    },

    async onClickCommentBtn() {
      await api.post(`/comment/create/COMMUNITY/${this.id}`, {
        writer: this.userId,
        content: this.commentInput,
      })
          .then((res) => {
            if (res.data.resultCode === "SUCCESS") {
              // this.$router.push({name: "BoardDetail", params: {id: this.id}});
              alert("댓글이 등록되었습니다.");
              this.fetchBoardDetail();
            } else {
              alert("댓글 등록 실패");
            }
          }).catch((err) => {
        console.log(err);
        alert("댓글 등록 실패");
      })
    }

  },

}

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
