<template>
  <div class="container card" v-if="comments.length !== 0">
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments" :key="comment.id">
        <div>
          <p>
            <strong>{{ comment.email }}</strong>
          </p>
          <small>{{ comment.body }}.</small>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import AppMainText from "./AppMainText.vue"
export default {
  props: ["comments"],
};
</script>