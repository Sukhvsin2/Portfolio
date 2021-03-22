<template>
  <b-container>
    <b-row>
      <b-col>
        <CollaborateCard :title="data[0].title" :tagline="data[0].tagline" :desc="data[0].desc">
          <div class="action">
            <b-button variant="outline-primary">
              <a href="/Resume.pdf" download="" target="__blank">Resumé</a>
            </b-button>
            <b-button variant="outline-primary">
              Work with me
            </b-button>
          </div>
        </CollaborateCard>
      </b-col>
      
      <b-col>
        <CollaborateCard :title="data[1].title" :tagline="data[1].tagline" :desc="data[1].desc">
          <div class="action">
            <b-button variant="outline-primary">Let's Chat</b-button>
          </div>
        </CollaborateCard>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data(){
    return{
      data: [
        {
          title: 'Skills',
          tagline: 'Complext web apps', 
          desc: "I'm really good at this, and have been doing it for a while.Specialties include EmberJS, VueJS, and Ruby on Rails.I've also used React, Elixir, Django, Node, and Scheme, and will learn other tech if necessary."
        },
        {
          title: 'Intrest',
          tagline: 'Let\'s build the future!', 
          desc: "Not an expert, but excited to get involved.I'm particularly interested in neighborhood planning, sustainable communities and land use, and health.Reach out to me if you're doing cool stuff - especially if you're in the Austin area."
        }
      ]
    }
  }

}
</script>

<style scoped>
.container{
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.action{
  text-align: center;
}

button{
  text-transform: capitalize;
}

</style>