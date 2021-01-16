<template>
   <div class="container">    
      <button class="btn primary" @click="$emit('loadComments')">Загрузить комментарии</button>   
   </div>
</template>

<script>
export default {
emits : ['loadComments']
}
</script>