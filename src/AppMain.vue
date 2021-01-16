<template>
  <div class="card card-w70" v-if="content.length !== 0">
    <div v-for="(item, idx) in content" :key="idx">
      <app-main-title
        v-if="item.typeOfBlock === 'title'"
        :content="item.contentOfBlock"
      ></app-main-title>
      <app-main-subtitle
        v-if="item.typeOfBlock === 'subtitle'"
        :content="item.contentOfBlock"
      ></app-main-subtitle>
      <app-main-avatar
        v-if="item.typeOfBlock === 'avatar'"
        :content="item.contentOfBlock"
      ></app-main-avatar>
      <app-main-text
        v-if="item.typeOfBlock === 'text'"
        :content="item.contentOfBlock"
      ></app-main-text>
    </div>
  </div>
  <div class="card card-w70" v-else>
    <h3>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import appMainTitle from "./AppMainTitle";
import appMainSubtitle from "./AppMainSubtitle";
import appMainAvatar from "./AppMainAvatar";
import appMainText from "./AppMainText";
import AppMainAvatar from "./AppMainAvatar.vue";

export default {
  props: ["content"],

  components: {
    appMainTitle,
    appMainSubtitle,
    appMainAvatar,
    appMainText,
  },
}
</script>

<style>
</style>