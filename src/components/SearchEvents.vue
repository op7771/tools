<template>
  <v-container fluid pa-2>
    <v-layout row>
      <v-flex lg12>
        <v-card color="grey lighten-4" pa-2 elevation-2>
          <v-card-title>
            <span class="headline">Search</span>
          </v-card-title>
          <div class="pl-2">
            <v-form ref="form">
              <v-select
                v-model="search_item.events"
                :items="events"
                attach
                chips
                deletable-chips
                label="Events"
                multiple
              ></v-select>
              <v-select
                v-model="search_item.gender"
                :items="genders"
                attach
                chips
                deletable-chips
                label="Genders"
                multiple
              ></v-select>

              <v-text-field dense type="number" suffix="Seconds" label="Pre-Duration"
                            v-model="search_item.preDuration"></v-text-field>
              <v-text-field dense type="number" suffix="Seconds" label="Post-Duration"
                            v-model="search_item.postDuration"></v-text-field>

              <v-menu
                v-model="picker"
                :close-on-content-click="false"
                :nudge-right="40"
                lazy
                transition="scale-transition"
                offset-y
                full-width
                min-width="290px"
              >
                <template v-slot:activator="{ on }">
                  <v-text-field
                    v-model="search_item.startDate"
                    label="Picker without buttons"
                    prepend-icon="mdi-calendar-clock"
                    readonly
                    v-on="on"
                  ></v-text-field>
                </template>
                <v-date-picker v-model="search_item.startDate" @input="picker = false"></v-date-picker>
              </v-menu>

              <v-menu
                v-model="picker2"
                :close-on-content-click="false"
                :nudge-right="40"
                lazy
                transition="scale-transition"
                offset-y
                full-width
                min-width="290px"
              >
                <template v-slot:activator="{ on }">
                  <v-text-field
                    v-model="search_item.endDate"
                    label="Picker without buttons"
                    prepend-icon="mdi-calendar-clock"
                    readonly
                    v-on="on"
                  ></v-text-field>
                </template>
                <v-date-picker v-model="search_item.endDate" @input="picker2 = false"></v-date-picker>
              </v-menu>

              <v-text-field label="Device" v-model="search_item.deviceId"></v-text-field>
              <v-checkbox v-model="search_item.justDeleted" :label="`Just Deleted event`"></v-checkbox>
              <v-btn @click="submit" right>Search</v-btn>
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
        justDeleted: false, preDuration: 2, postDuration: 2, startDate: '', endDate: ''
      },
      picker: false,
      picker2: false,
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
