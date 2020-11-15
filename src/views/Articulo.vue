<template>
  <div>
      <Titulo texto="ruta con parámetros" />
      <h2>Parámetro {{$route.params.id}}</h2>
      <p>{{details.body}}</p>
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
            details: {},
        }
    },
    methods: {
        async consumirApiById() {
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const response = await data.json()
                this.details = response
            } catch (error) {
                this.details = {}
            }
        },
    },
    created() {
        this.consumirApiById()
    }
}
</script>

<style>

</style>