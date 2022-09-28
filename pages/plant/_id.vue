   <template>
      <div>
        <h1>{{ plant.name }}</h1>
        <h2>{{ plant.scientificName }}</h2>
        <div>
          <div>
            <img :src="plant.img" alt="plant.name">
          </div>
          <div>
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