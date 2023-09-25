<template>
  <div class="container mt-2">
    <h2>Article: {{ id }}</h2>
    <h3>{{title}}</h3>
    <img :src="img" alt="image" width="700" height="393">
    <p class="mt-2">{{content}}</p>
    <button class="btn btn-sm btn-success rounded" @click="goBack">Go Back</button>
  </div>
</template>
<script>
export default {
    props: ["title", "img", "content"],
    data() {
        return {
            id: this.$route.params.title
        }
    },
    methods: {
      goBack() {
        this.$router.go(-1)
      }
    }
}
</script>