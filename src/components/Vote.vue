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
  components: {},
  data: function() {
    return {
      emoticons: ["very-bad", "bad", "oke", "good", "very-good"],
      isDisable: false,
      emoteClick: false
    };
  },
  methods: {
    vote(e) {
      this.isDisable = true;
      var voted = e.target.value;
      this.emoteClick = voted;
      var KeyStorage = moment().format("YYYYMMDDhhmmss ");
      var create_at = moment().format("YYYY-MM-DD hh:mm:ss ");
      var data = {
        vote: voted,
        create_at: create_at
      };
      var jsonTooString = JSON.stringify(data);
      localStorage.setItem(KeyStorage, jsonTooString);
    }
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
