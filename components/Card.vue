<template>
    <b-row class="p-3">
        <b-col class="my-2" v-for="(data, i) in content" :key="i"  v-show="data.category.indexOf(selected) != -1 ? true : false" cols="12" lg="4" md="6" sm="12">
            <b-card :title="data.title" :sub-title="data.type">
                <b-card-text>{{data.content}}</b-card-text>
                <b-button v-if="data.link != null" :href="data.link" target="__blank">Check it out</b-button>
            </b-card>
        </b-col>
    </b-row>
</template>

<script>
export default {
    props: ['content', 'selected']


}
</script>

<style scoped>
.card{
    height: 100%;
}
</style>