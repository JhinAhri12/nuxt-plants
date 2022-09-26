  <template>
      <div>
        <h1>Plant #{{ id }}</h1>
      </div>
    </template>
    <script>
    export default {
      head() {
        return {
          title: 'Plant #' + this.id,
          meta: [
            {
              hid: 'description',
              name: 'description',
              content: 'What you need to know about Plant #' + this.id
            }
          ]
        }
      },
      computed: {
        id() {
          return this.$route.params.id
        }
      }
    }
    </script>