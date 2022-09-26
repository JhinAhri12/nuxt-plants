<template>
  <div>
    <h1>Plants</h1>
    <PlantCard
      v-for="(plant, id) in plants"
      :key="id"
      :plant="plant"
      :data-index="id"
    />
  </div>
</template>
<script>
import PlantCard from '@/components/PlantCard.vue'
export default {
  name: "IndexPage",
  head(){
    return {
      title: 'Plant Listing'
    }
  },
  asyncData({ $axios }) {
    return $axios.get("http://localhost:3000/plants").then((response) => {
      return {
        plants: response.data,
      };
    }).catch(e => {
          error({ statusCode: 503, message: 'Unable to fetch plants at this time, please try again' })
  })
  },
  components: {
    PlantCard
  }
};
</script>
<style scoped>
    div {
      padding: 20px;
      margin-bottom: 24px;
      transition: all 0.2s linear;
      cursor: pointer;
    }
    div:hover {
      transform: scale(1.01);
      box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
    }
    .title {
      margin: 0;
      color: black;
    }
    a {
      text-decoration: none;
    }
    </style>