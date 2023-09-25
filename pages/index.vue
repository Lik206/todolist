<template>
  <div>
    <NavbarHeader />
    <div id="article" class="container">
      <h3 class="mt-3">Article</h3>
      <hr />
      <div v-for="article in articles" :key="article.title">
        <div class="media position-relative mb-4">
          <img :src="article.img" class="mr-3 rounded" alt="img" width="200" />
          <div class="media-body">
            <h5 class="mt-0">{{ article.title }}</h5>
            <p>
              {{ article.content }}
            </p>
            <nuxt-link
              :to="{
                name: 'article-id',
                params: {
                  title: article.title,
                  content: article.content,
                  img: article.img,
                },
              }"
              >Continue reading...</nuxt-link
            >
          </div>
        </div>
      </div>
    </div>

    <Todolist />
  </div>
</template>

<script>
import NavbarHeader from '../components/NavbarHeader.vue'
import Todolist from '@/components/TodoList.vue'

export default {
  name: 'IndexPage',
  components: {
    NavbarHeader,
    Todolist,
  },
  data() {
    return {
      articles: [
        {
          title: 'Judul Artikel 1',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1649282806617-c51bb282899c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80',
        },
        {
          title: 'Judul Artikel 2',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1635732646038-0a1a2fe3f2d6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1074&q=80',
        },
        {
          title: 'Judul Artikel 3',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1640006807976-a6127e9d6fa0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1171&q=80',
        },
      ],
    }
  },
}
</script>

