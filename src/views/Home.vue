<template>
  <div class="container">
    <section class="vote">
      <h3 class="give-your-vote">
        Silahkan berikan penilaian anda terhadap pelayanan kami
      </h3>
      <div class="emoticons">
        //ini akan menjadi komponen vote
      </div>
    </section>

    <section class="finish">
      <h4>Terima kasi telah memberikan penilaian anda</h4>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {}
};
</script>

<style type="text/css" scoped>
.container {
  display: flex;
  height: 100px;
  flex-wrap: wrap;
  color: #fff;
  align-items: center;
}
section {
  width: 100%;
}
</style>
