<template>
    <b-card :title="title" :sub-title="type">
        <b-card-text>{{content}}</b-card-text>
        <b-button v-if="link != null" :href="link" target="__blank">Visit</b-button>
    </b-card>
</template>

<script>
export default {
    props: ['title', 'content', 'link', 'type'],


}
</script>

<style scoped>
.card{
    height: 100%;
}
</style>