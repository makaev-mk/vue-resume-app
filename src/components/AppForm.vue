<template>
  <form class="card card-w30" @submit.prevent="Added">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="text"></textarea>
    </div>

    <button class="btn primary" :disabled="text.length < 3">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ['added'],
  data() {
    return {
      type: 'title',
      text: ''
    }
  },
  methods: {
    Added() {
      this.$emit('added', {
        type: this.type,
        text: this.text,
        id: Date.now()
      })
      console.log(this.type,this.text,Date.now())
      this.text = ''
      this.type = 'title'
    }
  }
}
</script>

<style scoped>

</style>
