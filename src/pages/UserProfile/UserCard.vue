<template>
  <md-card class="md-card-profile">
    <div class="md-card-avatar">
       <img class="img" :src="cardUserImage">
    </div>

    <md-card-content>
      <h6 class="category text-gray">Office Clerk</h6>
      <h4 class="card-title">Mae Anne G. David</h4>
      <md-button class="md-round md-error" @click="signOut">Sign Out</md-button>
    </md-card-content>
  </md-card>
</template>
<script>
export default {
  name: 'user-card',
  props: {
    cardUserImage: {
      type: String,
      default: require('@/assets/img/tsu-logo.png')
    }
  },
  data () {
    return {
    }
  },
  methods: {
    async signOut () {
      this.$router.push('/login')
    }
  }
}

</script>
<style>

</style>
