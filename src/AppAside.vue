<template>
    <form class="card card-w30" @submit.prevent="submitHandler">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="typeOfBlock">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="contentOfBlock"></textarea>
      </div>

      <button type="submit" class="btn primary" :disabled="check">Добавить</button>
    </form>
</template>

<script>
export default {
  data () {
    return {
      typeOfBlock: 'title',
      contentOfBlock: ''
    }    
  },
  emits: ['submitHandler'],
methods: {
  submitHandler () {
    this.$emit('submitHandler', {
      typeOfBlock: this.typeOfBlock,
      contentOfBlock: this.contentOfBlock
    })
    this.typeOfBlock = 'title'
    this.contentOfBlock = ''
  }
},
computed: {
  check () {
    return this.contentOfBlock.length < 4 ? true : false
  }
}
}
</script>

<style>

</style>