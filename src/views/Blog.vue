<template>
  <div>
      <Titulo texto="Titulo de mi blog"/>
      <!-- <button @click="consumirApi">Consumir API</button> -->
      <div v-for="blog in arrayBlog" :key="blog.id">
        <router-link :to="`/blog/${blog.id}`">
          <p>{{ blog.title }}</p>
        </router-link>
      </div>
  </div>
</template>

<script>
import Titulo from '../components/Titulo';

export default {
    components: {
        Titulo,
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async consumirApi() {
            try {
                const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                const array = await data.json()
                this.arrayBlog = array
            } catch (error) {
                this.arrayBlog = []
            }
        },
    },
    created() {
        this.consumirApi()
    }
}
</script>

<style>

</style>