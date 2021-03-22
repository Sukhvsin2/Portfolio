<template>
    <b-card :title="title">
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
</style>