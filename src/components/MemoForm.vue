<template>
  <div>
    <h5>ようこそ、{{ name }}さん</h5>
    <form @submit.prevent="postMemo">
      <label for="memo">メモ</label>
      <div>
        <textarea id="memo" cols="30" rows="10" v-model="memo.text"></textarea>
      </div>
      <span v-if="error.inValid">メモを入力してください</span>
      <div>
        <button type="submit">メモる</button>
      </div>
    </form>
    <MemoList :items="this.memoList" @delete="deleteMemo"/>
    <RouterLink to="/">トップに戻る</RouterLink>
  </div>
</template>

<script>
import MemoList from "./MemoList";
export default {
  components: {
    MemoList
  },
  computed: {
    name() {
      return this.$store.getters["name"];
    }
  },
  data() {
    return {
      memo: {
        id: null,
        text: ""
      },
      error: {
        inValid: false
      },
      memoList: {
        memos: []
      }
    };
  },
  methods: {
    postMemo() {
      if (this.memo.text === "") {
        this.error.inValid = true;
        return;
      } else {
        this.error.inValid = false;
      }
      const text = this.memo.text;
      const memosLength = this.memoList.memos.length;
      this.memoList.memos.push({
        id: memosLength === 0 ? 0 : this.memoList.memos[memosLength - 1].id + 1,
        text: text
      });
      this.memo.text = "";
    },
    deleteMemo(memoId) {
      const afterMemos = this.memoList.memos.filter(memo => {
        return memo.id !== memoId;
      });
      this.memoList.memos = afterMemos;
    }
  }
};
</script>

