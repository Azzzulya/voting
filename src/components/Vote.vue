<template>
  <div class="buttons">
    <button
      v-for="(emoticon, index) in emoticons"
      :key="index"
      :id="emoticon"
      :value="emoticon"
      :disabled="isDisable"
      class="btn-emoticon"
      :class="{ active: emoticon == emoteClick }"
      @click="vote"
    ></button>
  </div>
</template>

<script>
// @ is an alias to /src
import moment from "moment";

export default {
  name: "Vote",
  props: {
    voteProp: {
      type: Function
    }
  },
  data: function() {
    return {
      emoticons: ["very-bad", "bad", "oke", "good", "very-good"],
      emoteClick: ""
    };
  },
  methods: {
    vote(e) {
      var voted = e.target.value;
      //untuk menentukan buton dengan class aktif dan disbale semua button
      this.emoteClick = voted;
      //melakukan penyimpanan data ke store
      this.store(voted);
      //menerima indikator ke home component unutk menampilan terima kasih
      this.voteProp();
    },
    store(voted) {
      var KeyStorage = moment().format("YYYYMMDDhhmmss ");
      var created_at = moment().format("YYYY-MM-DD hh:mm:ss ");
      var data = {
        vote: voted,
        created_at: created_at
      };
      var jsonTooString = JSON.stringify(data);
      localStorage.setItem(KeyStorage, jsonTooString);
    }
  },
  computed: {
    isDisable: function() {
      return this.emoteClick.length === 0 ? false : true;
    }
  },
  mounted() {
    this.$root.$on("emitProcessDone", () => {
      this.emoteClick = "";
    });
  }
};
</script>

<style type="text/css">
.buttons {
  display: flex;
}
.btn-emoticon {
  text-align: center;
  background: url("~@/assets/emoticon.png");
  width: 100px;
  height: 100px;
  border: none;
  margin: 0px 10px;
  outline: none;
  cursor: pointer;
}

#very-bad {
  background-position: 0px 0px;
}
#very-bad:hover {
  background-position: 0px -100px;
}
#very-bad.active,
#very-bad:active {
  background-position: 0px -200px;
}
#bad {
  background-position: 101px 0px;
}
#bad:hover {
  background-position: 101px -100px;
}
#bad.active,
#bad:active {
  background-position: 101px -200px;
}
#oke {
  background-position: 201px 0px;
}
#oke:hover {
  background-position: 201px -100px;
}
#oke.active,
#oke:active {
  background-position: 201px -200px;
}
#good {
  background-position: 301px 0px;
}
#good:hover {
  background-position: 301px -100px;
}
#good.active,
#good:active {
  background-position: 301px -200px;
}
#very-good {
  background-position: 401px 0px;
}
#very-good:hover {
  background-position: 401px -100px;
}
#very-good.active,
#very-good:active {
  background-position: 401px -200px;
}
</style>
