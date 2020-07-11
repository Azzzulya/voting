<template>
  <div class="container">
    <section class="vote">
      <h3 class="give-your-vote">
        Silahkan berikan penilaian anda terhadap pelayanan kami
      </h3>
      <div class="emoticons">
        <Vote />
      </div>
    </section>

    <section class="finish">
      <h4>Terima kasi telah memberikan penilaian anda</h4>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import Vote from "@/components/Vote.vue";

export default {
  name: "Home",
  components: {
    Vote
  }
};
</script>

<style type="text/css">
.container {
  display: flex;
  height: 100%;
  flex-wrap: wrap;
  color: #fff;
  align-items: center;
}
.emoticons {
  display: flex;
  justify-content: center;
}

section {
  width: 100%;
}
.give-your-vote {
  font-size: 25px;
}
.finish {
  position: absolute;
  bottom: 20px;
}
</style>
