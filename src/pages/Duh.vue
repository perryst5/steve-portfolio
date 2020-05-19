<template>
  <Layout>
    <audio id="duh">
      <source src="/duh.mp3">
    </audio>
    <button onclick="document.getElementById('duh').play();">Duh</button>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Duh'
  }
}
</script>

<style>
</style>
