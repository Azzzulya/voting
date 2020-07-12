<template>
  <div class="container">
    <section class="vote">
      <h3 class="give-your-vote">
        Silahkan berikan penilaian anda terhadap pelayanan kami
      </h3>
      <div class="emoticons">
        <Vote :voteProp="vote" />
      </div>
    </section>

    <section class="finish">
      <transition name="fade" v-on:after-enter="afterClick">
        <h4 v-if="show">Terima kasi telah memberikan penilaian anda</h4>
      </transition>
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
  },
  methods: {
    vote() {
      this.show = true;
    },
    afterClick() {
      this.show = false;
      this.$root.$emit("emitProcessDone");
    }
  },
  data: function() {
    return {
      show: false
    };
  }
};
</script>

<style type="text/css">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
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
