<template>
  <div>
    <md-table v-model="documentsState10" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Time Posted">{{ item.prev_release }}</md-table-cell>
        <md-table-cell md-label="Tracking number">{{ item.tracking_number }}</md-table-cell>
        <md-table-cell md-label="Title">{{ item.title }}</md-table-cell>
        <md-table-cell md-label="Author">{{ item.authors }}</md-table-cell>
        <md-table-cell md-label="Action">
            <md-button class="md-raised md-success" @click.native="receiveDocument(item.id)">Recieve</md-button>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'res-from-fr3',
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
      documentsState10: []
    }
  },
  created: async function () {
    await this.getDocuments()
  },
  methods: {
    getDocuments: async function () {
      const rootApi = process.env.VUE_APP_API_ROOT
      this.documents = (await axios.get(`${rootApi}/documents`)).data
      this.documentsState10 = this.documents.filter(d => d.state === 10 && d.received === null)
    },
    receiveDocument: async function (documentId) {
      const rootApi = process.env.VUE_APP_API_ROOT
      await axios.post(`${rootApi}/documents/${documentId}/receive`)
      await this.getDocuments()
    }
  }
}
</script>
