<template>
  <b-card class="card">
      <div class="title">{{title}}</div>
      <div class="focus">{{tagline}}</div>
      <p class="description">{{desc}}</p>
      <slot></slot>
  </b-card>
</template>

<script>
export default {
    props: ['title', 'tagline', 'desc']

}
</script>

<style scoped>
.card{
  min-height: 300px !important;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.title{
  color: #0984e3;
  font-size: 1.5rem;
  font-weight: bold;
  text-align: center;
}
.focus{
  font-size: 2rem;
  font-weight: bolder;
  text-align: center;
}
.description{
  font-size: 1rem;
  margin: 8px auto;
}
</style>