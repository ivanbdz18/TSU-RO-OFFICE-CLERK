<template>
  <div class="content">
    <div class="md-layout">
       <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="md-title">Outgoing Research proceeding to Department Research Coordinator</h4>
            <p class="category">List of Documents</p>
          </md-card-header>
          <md-card-content>
            <crec-to-drc class="md-body-2" table-header-color="orange"></crec-to-drc>
          </md-card-content>
        </md-card>
      </div>
      <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="md-title">Outgoing Research proceeding to URO</h4>
            <p class="category">List of Documents</p>
          </md-card-header>
          <md-card-content>
            <urec-to-uro class="md-body-2" table-header-color="orange"></urec-to-uro>
          </md-card-content>
        </md-card>
      </div>
      <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="md-title">Outgoing Research proceeding to FR</h4>
            <p class="category">List of Documents</p>
          </md-card-header>
          <md-card-content>
            <rerc-to-fr class="md-body-2" table-header-color="orange"></rerc-to-fr>
          </md-card-content>
        </md-card>
      </div>
      <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="md-title">Outgoing Research proceeding to URO</h4>
            <p class="category">List of Documents</p>
          </md-card-header>
          <md-card-content>
            <oup-to-uro class="md-body-2" table-header-color="orange"></oup-to-uro>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import {
  CrecToDrc,
  OupToUro,
  RercToFr,
  UrecToUro
} from '@/components'

export default{
  components: {
    CrecToDrc,
    OupToUro,
    RercToFr,
    UrecToUro
  },
  data () {
    return {

    }
  }
}
</script>
