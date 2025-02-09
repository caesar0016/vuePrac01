<script>
  export default{
    data(){
      return {
        name: 'Hu Tao',
        youLikeher: 'No',
        gender: 'Female',
        height: 'medium',
        supports: ['Xing Qiu', 'Furina', 'Xilonen'],
        links: 'https://game8.co/games/Genshin-Impact/archives/314347'
      };
    },
    methods:{
      toggleLike(){

        if(this.youLikeher === 'Yes'){

          this.youLikeher = 'No';

        }else if(this.youLikeher === 'No'){

          this.youLikeher = 'Yes';

        }else{

          this.youLikeher = 'Yes';

        } 
      }
    }
  };
</script>

<template>  
  <h1>Genshin Daily</h1>
  <h1> Name: {{ name }}</h1>
  <p v-if="youLikeher === 'Yes'">Do I like Hu Tao? {{ youLikeher }}</p>
  <p v-else-if="youLikeher === 'No'">Do I like Hu Tao? {{ youLikeher }}</p>
  <p v-else="youLikeher">No Comment</p>

  <h3>Supports:</h3>
  <ul>
    <li v-for="character in supports" :key="supp01">{{ character }}</li>
  </ul>
  <!-- <a v-bind:href="links">See more for Hu Tao</a> -->
  <a :href="links">See more for Hu Tao</a>

  <div>

    <button @click="toggleLike">Click to like hu tao</button>
  </div>
</template>