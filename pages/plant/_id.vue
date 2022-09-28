   <template>
      <div>
        
        <div class="plant-overflow">
          <div class="plant-infos">
            <h1>{{ plant.name }}</h1>
            <h2><i>{{ plant.scientificName }}</i></h2>
          </div>
          <div>
            <img :src="plant.img" alt="plant.name">
          </div>
          <div class="plant-desc">
            {{plant.description}}
          </div>
        </div>
      </div>
    </template>
    <script>
    export default {
      head() {
        return {
          title: this.plant.name,
          meta: [
            {
              hid: 'description',
              name: 'description',
              content: 'What you need to know about ' + this.plant.name
            }
          ]
        }
      },
      async asyncData({ $axios, error, params }) {
        try {
          const { data } = await $axios.get(
            'http://localhost:3000/plants/' + params.id
          )
          return {
            plant: data
          }
        } catch (e) {
          error({
            statusCode: 503,
            message: 'Unable to fetch plant #' + params.id
          })
        }
      }
    }
    </script>
    <style scoped>
    h2{
      color:#39b982;
    }
    .plant-desc {
        padding: 16px;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  position: relative;
  color:grey;
    }
    .plant-overflow{
        overflow: hidden;
  background: white;
  box-shadow: 0 0 15px rgba(0,0,0,0.2);
    }
    .plant-infos{
      padding: 12px;
    }
    </style>