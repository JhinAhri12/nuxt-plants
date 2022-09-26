<template>
  <div>
    <h1>Plants</h1>
    
  </div>
</template>
<script>
export default {
  name: "IndexPage",
  asyncData({ $axios }) {
    return $axios.get("http://localhost:3000/plants").then((response) => {
      return {
        plants: response.data,
      };
    });
  },
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