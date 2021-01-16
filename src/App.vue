<template>
  <div class="container column">
    <app-aside @submitHandler="submitHandler"></app-aside>
    <app-main :content="contentMain"></app-main>
  </div>
  <div :style="{ display: isVisible ? 'block' : 'none' }">
    <app-btn-apload @loadComments="loadComments"></app-btn-apload>
  </div>

  <app-loader v-if="loading"></app-loader>
  <app-comments v-else :comments="comments"></app-comments>
</template>

<script>
import AppAside from "./AppAside"
import AppMain from "./AppMain"
import AppBtnApload from "./AppBtnApload"
import AppLoader from "./AppLoader"
import AppComments from "./AppComments"

export default {
  data() {
    return {
      contentMain: [],
      typeOfBlock: "",
      contentOfBlock: "",
      comments: [],
      loading: false,
      btnVisible: true,
      isVisible: true,
    };
  },
  methods: {
    submitHandler(data) {
      const typeOfBlock = (this.typeOfBlock = data.typeOfBlock)
      const contentOfBlock = (this.contentOfBlock = data.contentOfBlock)
      this.contentMain.push(data)
      console.log("contentMain", this.contentMain)
    },
    async loadComments() {
      this.loading = true;
      await fetch("https://jsonplaceholder.typicode.com/comments?_limit=42")
        .then((response) => response.json())
        .then((data) => {
          this.comments = Object.keys(data).map((key) => {
            return {
              id: key,
              email: data[key].email,
              body: data[key].body,
            }
          })
        })
        .catch((error) => console.error(error))
      this.isVisible = false
      this.loading = false
    },
  },
  components: {
    AppAside,
    AppMain,
    AppBtnApload,
    AppLoader,
    AppComments,
  },
};
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
