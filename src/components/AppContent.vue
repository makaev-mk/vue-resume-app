<template>
  <div class="card card-w70" >
    <template v-if="resumeData.length">
      <component
          v-for="block in resumeData"
          :key="block.id"
          :is="'resume-' + block.type"
          v-bind="{text: block.text}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from "./layouts/ResumeTitle"
import ResumeSubtitle from "./layouts/ResumeSubtitle"
import ResumeAvatar from "./layouts/ResumeAvatar"
import ResumeText from "./layouts/ResumeText"

export default {
  props: ['resumeData'],
  methods: {
    app(){
      console.log(1)
    }
  },
  components: {ResumeTitle, ResumeSubtitle, ResumeText, ResumeAvatar}
}
</script>

<style scoped>

</style>
