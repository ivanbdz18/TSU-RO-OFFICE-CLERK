<template>
  <div>
    <md-table v-model="documentsState13" :table-header-color="tableHeaderColor">
      <md-table-row class="md-body-2" slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Time Date">{{ item.time_date }}</md-table-cell>
        <md-table-cell md-label="Tracking No.">{{ item.tracking_number }}</md-table-cell>
        <md-table-cell md-label="Research Title">{{ item.title }}</md-table-cell>
        <md-table-cell md-label="Grade in Colloquium">{{ item.gradeCol }}</md-table-cell>
        <md-table-cell md-label="Grade in UREC">{{ item.gradeUrec }}</md-table-cell>
          <md-table-cell md-label="University Research Agenda">{{ item.agenda }}</md-table-cell>
        <md-table-cell md-label="Action">
          <md-button to="/comment" class="md-raised md-success">Comment</md-button>
          <md-button class="md-raised md-success" @click.native="proceed(item.id)">Proceed</md-button>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'oup-to-uro',
  props: {
    tableHeaderColor: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      selected: [],
      documents: [],
      documentsState13: []
    }
  },
  created: async function () {
    await this.getDocuments()
  },
  methods: {
    proceed: async function (documentId) {
      const rootApi = process.env.VUE_APP_API_ROOT
      await axios.post(`${rootApi}/documents/${documentId}/release`)
      await this.getDocuments()
    },
    getDocuments: async function () {
      const rootApi = process.env.VUE_APP_API_ROOT
      this.documents = (await axios.get(`${rootApi}/documents`)).data
      this.documentsState13 = this.documents.filter(d => d.state === 13 && d.received !== null)
    }
  }
}
</script>
