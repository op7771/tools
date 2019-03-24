<template>
  <v-container fluid pa-2>
    <v-layout row>
      <v-flex xs12>
        <v-card color="grey lighten-4" pa-2 elevation-2>
          <v-card-title>
            <span class="headline">Search</span>
          </v-card-title>
          <div class="pl-2">
            <v-form ref="form" v-model="search_item">
              <v-select
                dense
                v-model="search_item.events"
                :items="events"
                attach
                chips
                deletable-chips
                label="Events"
                multiple
              ></v-select>
              <v-select
                dense
                v-model="search_item.gender"
                :items="genders"
                attach
                chips
                deletable-chips
                label="Genders"
                multiple
              ></v-select>
              <v-checkbox v-model="search_item.justDeleted" :label="`Just Deleted event`"></v-checkbox>
              <v-text-field label="Device" v-model="search_item.deviceId"></v-text-field>

              <v-btn @click="submit">submit</v-btn>
            </v-form>
          </div>

        </v-card>

      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: 'SearchEvents',
  data () {
    return {
      search_item: {
        justDeleted: false
      },
      events: ['SVC', 'PVC'],
      genders: ['Female', 'Male'],
      deviceId: ''
    }
  },
  methods: {
    submit () {
      console.log(this.search_item)
    }
  }
}
</script>

<style scoped>

</style>
