<template>
  <b-container fluid>
      <b-row>
          <b-col cols="12" lg="2" md="2" sm="2" class="optionSection pt-3">
              <div class="mt-2 options">
                  <b-button block :variant="active == 'all' ? 'outline-secondary' : 'link'"  @click="urlChange('all')">All</b-button>
                  <div class="sectionDesc">filter by activity</div>
                  <b-button block :variant="active == 'company' ? 'outline-secondary' : 'link'" @click="urlChange('company')">Company</b-button>
                  <b-button block :variant="active == 'personal' ? 'outline-secondary' : 'link'" @click="urlChange('personal')">Personal</b-button>
                  <div class="sectionDesc">filter by tools</div>
                  <b-button block :variant="active == 'backend' ? 'outline-secondary' : 'link'" @click="urlChange('backend')">Backend</b-button>
                  <b-button block :variant="active == 'frontend' ? 'outline-secondary' : 'link'"  @click="urlChange('frontend')">Frontend</b-button>
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
                <Card :content="content" :selected="active" />
          </b-col>
      </b-row>
  </b-container>
</template>

<script>
export default {
    head(){
        return{
            title: 'Projects'
        }
    },
    data(){
        return{
            active: 'all',
            order: 'recent',
            categories:[{name: 'all'}, {name: 'company'}, {name: 'personal'}, {name: 'backend'}, {name: 'frontend'}],
            content: [
                {title: 'Aussie Pet', content: 'I started this project while I was on internship for booking pet services. As a frontend engineer, I designed whole UI on VueJS. And, build functionality like: Messaging, Booking, Shopping for Pet Food, Dating.', link: null, type: 'May - Nov 2020 | Company', category: ['company', 'frontend', 'all']},
                {title: 'AirBnb Clone', content: 'This is a clone of AirBnb UI, Made with ReactJS!!', link: 'https://aurbnbreactjs.netlify.app/', type: '2020 Arpil | UI', category: ['frontend', 'personal', 'all']},
                {title: 'Chatting Website', content: 'This project is an example of how web sockets work while we text eachother in realtime. This is built using ReactJS & ExpressJS for server.', link: 'https://socket-react-app.netlify.app/', type: 'June 2020 | Personal', category: ['personal', 'frontend', 'all']},
                {title: 'Resume Editor', content: 'This Project was on NuxtJS. I made resume editor like novo resume for the company. I used Vuex Store for state management, Vuetify & Vuesax for UI framework.', link: null, type: 'Feb - May 2020 | Company', category: ['comapany', 'fronend', 'all']},
                {title: 'Face Filter', content: 'This was project I started after my training in Machine Learning with python, I created a face filter like snapchat with OpenCV.', link: null, type: '2019 May | Personal', category: ['personal', 'all']},
                {title: 'Face Attendance Syatem', content: 'This was the project I worked for my department at Univeristy. Build a attendance system with face recognition with python & OpenCV.', link: null, type: 'Sep 2019 | University', category: ['university', 'personal', 'all']},
                {title: 'Income Expense API', content: 'Django Based REST API project from scratch with drf framework. All api\'s with stats data of user\'s income & expense.', link: null, type: 'Dec 2020 | Personal', category: ['backend', 'personal', 'all']},
                {title: 'Streaming Application', content: 'Built in flutter with NodeJs backend, i worked as frontend developer & built whole UI. This porject was application that consume videos from backend realtime.', link: null, type: 'Feb 2020 | Company', category: ['company', 'frontend', 'all']},
                {title: 'Hulu Clone', content: 'Website built on ReactJs, consuming api from MoviesHD. Recommending movies according to selction & provding information from rating to reviews.', link: null, type: 'March 2020 | Personal', category: ['frontend', 'personal', 'all']},
                {title: 'Money Transfer App', content: 'Started while I was intern, built in React Native. Project was building a money transfer app with user stats, qr money sharing functionality, saving, etc.', link: null, type: 'Nov 2020 | Company', category: ['company', 'frontend', 'all']},
                {title: 'School Management System', content: 'School Management System build on Nuxt.Js, with functionality of role like: admin, principal, teacher, student accounts.', link: null, type: 'Nov 2020 | Company', category: ['company', 'frontend', 'all']},
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
    background-color: #f1f2f6;
}
.options > button{
    color: white
}
.optionSection{
    background-color: #00b894;
    height: 100vh;
    overflow: auto;
}
@media (max-width: 760px) {
    .optionSection{
        display: none;
    }
}
.optionDetails{
    padding-left: 25px;
    height: 100vh;
    overflow: auto;
}
.sectionDesc{
    text-transform: uppercase;
    text-align: center;
    font-weight: 600;
    margin-top: 10px;
    font-size: 0.9rem;
}
button{
    text-align: left;
}
.options{
    position: sticky;
    top: 25px;
}

</style>