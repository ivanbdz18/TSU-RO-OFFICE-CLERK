<template>
  <div>
    <md-table v-model="documentsState4" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Time Date">{{ item.received }}</md-table-cell>
        <md-table-cell md-label="Tracking No.">{{ item.tracking_number }}</md-table-cell>
        <md-table-cell md-label="Research Title">{{ item.title }}</md-table-cell>
        <md-table-cell md-label="Authors">{{ item.authors }}</md-table-cell>
        <md-table-cell md-label="Action">
          <md-button class="md-just-icon md-simple md-primary">
            <md-icon>get_app</md-icon>
            <md-tooltip md-direction="top">Download</md-tooltip>
          </md-button>
          <md-button class="md-raised md-success" :to="`/comment?document=${item.id}&state=4`">Comment</md-button>
          <md-button class="md-raised md-success" @click.native="proceed(item.id)">Proceed</md-button>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'crec-to-uro',
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
      documentsState4: [
        {
          received: '05:56:15 08/11/18',
          tracking_number: '15ls1515-55d4-f3db',
          title: 'Vehicle Tracking Sytem for LTO',
          authors: 'Alex Gonzaga, Peter Cayetano'
        },
        {
          received: '04:25:45 08/08/18',
          tracking_number: '25jf5158-5s5d-sa15',
          title: 'POS for Bean On Me Cafe',
          authors: 'Peter Magdangal, Joshua Agustine'
        },
        {
          received: '04:12:05 08/08/18',
          tracking_number: '48ki1452-5f8g-sa5f',
          title: 'Online Ordering System for Cafroozo',
          authors: 'Peter Reyes, Marc Castro'
        },
        {
          received: '03:52:25 08/08/18',
          tracking_number: '45as2326-5s4d-f3db',
          title: 'Appointment System for Ramos Dental Clinic',
          authors: 'Manuel Navidad, Ivan Tongol'
        }
      ]
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
      this.documentsState4 = this.documents.filter(d => d.state === 4 && d.received !== null)
    }
  }
}
</script>
