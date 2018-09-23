<template>
  <form>
    <md-card>
      <md-card-content>
        <div class="md-layout">
          <div class="md-layout-item md-size-100">
            <md-field maxlength="5">
              <label>Message / Comment:</label>
              <md-textarea v-model="message"></md-textarea>
            </md-field>
          </div>
          <div class="md-layout-item md-size-100 text-right">
            <md-button @click="goBack" class="md-raised md-success">Go Back</md-button>
            <md-button @click="comment" class="md-raised md-success">Send</md-button>
          </div>
        </div>

      </md-card-content>
    </md-card>
  </form>
</template>
<script>
import axios from 'axios'
import store from './../../stores/store'

export default {
  name: 'comments',
  props: {
    dataBackgroundColor: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      message: ''
    }
  },
  methods: {
    goBack: function () {
      this.$router.go(-1)
    },
    comment: async function () {
      const data = {
        comment: this.message,
        commentor_id: store.getters.user.id
      }
      const rootApi = process.env.VUE_APP_API_ROOT
      try {
        await axios.post(`${rootApi}/documents/${this.$route.query.document}/state/${this.$route.query.state}/comments`, data);
        this.message = ''
      } catch (e) {
        
      }
      
    }
  }
}

</script>
