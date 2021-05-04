<template>
  <div class="container column">
    <AppForm @added="Added"/>
    <AppContent
        :resumeData="blocks"/>
  </div>
  <div class="container">
    <AppLoader v-if="loading"/>
    <AppComment
        v-else
        :comments="comments"
        @show-comments="loadComment"
    />
  </div>
</template>

<script>
import AppContent from "@/components/AppContent";
import AppComment from "@/components/AppComment";
import AppLoader from "@/components/AppLoader";
import AppForm from "@/components/AppForm";

export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    Added(block) {
      this.blocks.push(block)
      console.log(this.blocks)
    },
   async loadComment() {
     this.loading = true
     const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
     this.comments = await res.json()
     this.loading = false
   }
  },
  components: {AppLoader, AppContent, AppComment, AppForm}
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
