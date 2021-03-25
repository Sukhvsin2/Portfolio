<template>
  <b-container>
    <b-row>
      <b-col cols="12" lg="6" md="6" sm="12" class="my-2">
        <CollaborateCard :title="data[0].title" :tagline="data[0].tagline" :desc="data[0].desc">
          <div class="action">
            <b-button variant="outline-primary">
              <a href="/Resume.pdf" download="" target="__blank">Resumé</a>
            </b-button>
            <b-button variant="outline-primary" href="mailto:sukhvsingh2026@gmail.com?subject=Would youlike to work on _______?" target="_blank">
              Work with me
            </b-button>
          </div>
        </CollaborateCard>
      </b-col>
      
      <b-col cols="12" lg="6" md="6" sm="12" class="my-2">
        <CollaborateCard v-if="!chat" :title="data[1].title" :tagline="data[1].tagline" :desc="data[1].desc">
          <div class="action">
            <b-button variant="outline-primary" @click="chat = true">Let's Chat</b-button>
          </div>
        </CollaborateCard>
        <div v-else class="message">
          <b-card style="height: 100%;">
            <b-form @submit="formSubmit">
              <div class="title">
                Message
              </div>
              <b-form-input placeholder="Name" label="Name" class="my-3" v-model="name"></b-form-input>
              <b-form-textarea class="my-3 mb-4" v-model="message"></b-form-textarea>
              <b-button block class="mt-4" type="submit">
                Send
              </b-button>
            </b-form>
          </b-card>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import emailjs from "emailjs-com"
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
      ],
      chat: false,
      name: '',
      message: 'I\'m working on ...\nWant to join?'
    }
  },
  methods: {
    async formSubmit(e){
      e.preventDefault();
      const data = {
        name: this.name,
        message: this.message
      }
      try {
        const res = await emailjs.send('', 'template_61wn9zg', data, 'user_vBVXDgWn7FaijtxEm0G3m');
        console.log(res);
      } catch (error) {
        console.log(error);
      }
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

.title{
  font-size: 1.3rem;
  font-weight: 700;

}

.message{
  animation: 1s appear;
  height: 100%;
}

@keyframes appear {
  0% {
    opacity: 0;
  }
}

</style>