<template>
  <Layout>
    <div class="flex-page">
      <div>
        <h1>Car Lease Stats</h1>

        Today is: {{today}} <br>
        Lease Started on: {{startOfLease}} <br>
        Days into Lease: {{daysIntoLease}} ({{percentDaysIntoLease}}%)<br>
        On Track Miles Count: <strong>{{onTrackMilesCount}}</strong><br>
        Miles Left on Lease: {{milesToGo}}
      </div>
      <g-image src="~/assets/images/car.jpg" width="500"/>
    </div>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  data: function(){
    return {
      today: new Date().toLocaleDateString(),
      startOfLease: new Date("March 25, 2019").toLocaleDateString()
    }
  },
  computed:{
    daysIntoLease(){
      let today = new Date()
      let startOfLease = new Date("March 25, 2019")
      return Math.floor((today - startOfLease) / (60*60*24*1000))
    },
    percentDaysIntoLease(){
      let daysIntoLease = Math.floor((new Date() - new Date("March 25, 2019")) / (60*60*24*1000))
      return ((daysIntoLease / 1096) * 100).toFixed(1)
    },
    onTrackMilesCount(){
      let daysIntoLease = Math.floor((new Date() - new Date("March 25, 2019")) / (60*60*24*1000))
      let milesPerDay = 10000 / 365
      return Math.floor(daysIntoLease * milesPerDay)
    },
    milesToGo(){
      return 30000 - this.onTrackMilesCount
    }
  }
}
</script>

<style lang="scss" scoped>
.home-links a {
  margin-right: 1rem;
}
.flex-page{
  display: flex;
  justify-content: space-between;
  & > div{
    margin-right: 30px;

    h1{
      margin-top: 0;
      line-height: 1;
    }
  }

  img{
    max-width: 100%;
  }
}
</style>
