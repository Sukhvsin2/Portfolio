<template>
  <b-container fluid>
      <b-row>
          <b-col cols="12" lg="2" md="2" sm="2" class="optionSection pt-3">
              <div class="mt-2">
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
                  <b-col cols="4"><a href="/Resume.pdf" download="" target="__blank">Download Resume</a></b-col>
                  <b-col cols="4">Content2</b-col>
                  <b-col cols="4">Content3</b-col>
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
        }
    }

}
</script>

<style scoped>
.container-fluid{
    height: 100vh;
}
.optionSection{
    background-color: #a29bfe;
    height: 100vh;
}
.optionDetails{
    padding-left: 25px;
    height: 100vh;
}
.sectionDesc{
    text-transform: uppercase;
    text-align: center;
    margin-top: 10px;
    font-size: 0.9rem;
}
button{
    text-align: left;
}

</style>