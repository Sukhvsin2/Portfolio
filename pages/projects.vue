<template>
  <b-container fluid>
      <b-row>
          <b-col cols="12" lg="2" md="2" sm="2" class="optionSection pt-3">
              <div class="mt-2 options">
                  <b-button block :variant="active == 'all' ? 'outline-primary' : 'link'"  @click="urlChange('all')">All</b-button>
                  <div class="sectionDesc">filter by activity</div>
                  <b-button block :variant="active == 'company' ? 'outline-primary' : 'link'" @click="urlChange('company')">Company</b-button>
                  <b-button block :variant="active == 'personal' ? 'outline-primary' : 'link'" @click="urlChange('personal')">Personal</b-button>
                  <div class="sectionDesc">filter by tools</div>
                  <b-button block :variant="active == 'backend' ? 'outline-primary' : 'link'" @click="urlChange('backend')">Backend</b-button>
                  <b-button block :variant="active == 'frontend' ? 'outline-primary' : 'link'"  @click="urlChange('frontend')">Frontend</b-button>
              </div>
          </b-col>
          <b-col cols="12" lg="10" md="10" sm="12" class="optionDetails">
              <b-row class="mt-3 px-3">
                  <b-col cols="4">
                      <b-button variant="link" @click="$router.push('/')">Home</b-button>
                  </b-col>
                  <b-col cols="4">
                      <b-row><b-button v-for="(item,i) in categories" :key="`category${i}`" :variant="active == item.name ? 'outline-primary' : 'link'"  @click="urlChange(item.name)" size="sm">{{item.name}}</b-button></b-row>
                  </b-col>
                  <b-col cols="4">
                      <b-row style="text-align: right;">
                          <b-button :variant="order == 'recent' ? 'outline-primary' : 'link'" size="sm" class="ml-2" @click="sortProjects(active, 'recent')">Recent</b-button>
                          <b-button :variant="order == 'old' ? 'outline-primary' : 'link'" size="sm" class="ml-2" @click="sortProjects(active, 'old')">Old</b-button>
                      </b-row>
                  </b-col>
              </b-row>
              <b-row class="p-3">
                  <b-col class="my-2" v-for="(data, i) in content" :key="i" cols="12" lg="4" md="6" sm="12">
                    <Card :title="data.title" :content="data.content" :link="data.link" :type="data.type"/>
                  </b-col>
              </b-row>
          </b-col>
      </b-row>
  </b-container>
</template>

<script>
export default {
    data(){
        return{
            active: 'all',
            order: 'recent',
            categories:[{name: 'all'}, {name: 'company'}, {name: 'personal'}, {name: 'backend'}, {name: 'frontend'}],
            content: [
                {title: 'Title Check', content: 'This is content of this card!', link: 'null', type: 'company'},
                {title: 'Title Check 1', content: 'This is content of this card!', link: 'null', type: 'personal'},
                {title: 'Title Check 2', content: 'This is content of this card!', link: 'null', type: 'company'},
                {title: 'Title Check 3', content: 'This is content of this card!', link: 'null', type: 'company'},
                {title: 'Title Check 4', content: 'This is content of this card!', link: 'null', type: 'personal'},
                {title: 'Title Check 5', content: 'This is content of this card!', link: 'null', type: 'company'}
            ]
        }
    },
    mounted() {
        const data = this.$route.query
        if(data.filter == undefined) this.active = 'all'
        else this.active = data.filter
    },
    methods:{
        urlChange(value){
            this.$router.push({path: "/projects", query: {filter: value}})
            this.active = value
        },
        sortProjects(type, order){
            this.$router.push({path: '/projects', query: {filter: type, sort: order}})
            this.order = order
        }
    }

}
</script>

<style scoped>
.container-fluid{
    height: 100vh;
}
.options > button{
    color: white
}
.optionSection{
    background-color: #00b894;
    height: 100vh;
}
@media (max-width: 760px) {
    .optionSection{
        display: none;
    }
}
.optionDetails{
    padding-left: 25px;
    height: 100vh;
}
.sectionDesc{
    text-transform: uppercase;
    text-align: center;
    font-weight: 700;
    margin-top: 10px;
    font-size: 0.9rem;
}
button{
    text-align: left;
}

</style>