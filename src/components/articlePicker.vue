<template>
  <div>
    <h2>Choose your type of article</h2>

    <div>
      <div id="container" class="contentContainer">
        <div
          v-for="articles in articleArray"
          :key="articles"
          :class="{ icon: true, iconClicked: articles.selected }"
          @click="toggleArticle(articles)"
        >
          <i :class="articles.symbol" style="fontsize: 2rem"></i>
          <p>{{ articles.name }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},

  data: function () {
    return {
      toggleClick: false,
      chosenArticle: [],
      articleArray: [
        {
          id: 0,
          name: "Watches",
          symbol: "pi pi-clock",
          abbr: "watch",
          selected: false,
        },
        {
          id: 1,
          name: "Electrical Device",
          symbol: "pi pi-power-off",
          abbr: "eee",
          selected: false,
        },
        {
          id: 2,
          name: "Toys",
          symbol: "pi pi-android",
          abbr: "toy",
          selected: false,
        },
        {
          id: 3,
          name: "Leather good",
          symbol: "pi pi-inbox",
          abbr: "leather",
          selected: false,
        },
      ],
    };
  },
  methods: {
    toggleArticle: function (article) {
      for (let i = 0; i < this.articleArray.length; i++) {
        this.articleArray[i].selected = false;
      }
      this.articleArray[article.id].selected = true;
      this.$emit("submit-article", article.abbr);
    },
  },
};
</script>

<style scoped>


.icon {
  text-align: center;
  background: white;
  border: 5px double hsl(200, 30%, 30%);
  border-radius: 15%;
  height: 130px;
  width: 130px;
  margin: 10px 10px;
}
.icon i {
  align-self: center;

  font-size: 50px !important;
  margin-top: 10px;
  color: hsl(200, 30%, 30%);
}
.icon p {
  text-align: center;
  padding: 1px 1px;
 
  font-size: 15px;
  font-weight: bold;
  color: hsl(200, 30%, 30%);

  margin: 5px 5px 5px 5px;
}
.icon:hover p {
  color: limegreen;
}

.icon:hover i {
  color: limegreen;
}
.icon:hover {
  border: 3px limegreen solid;
  background: hsl(200, 30%, 30%);
  box-shadow: limegreen;
}

.iconClicked {
  border: 3px white solid;
  background: hsl(220, 20%, 30%);
  box-shadow: limegreen;
  transform: scale(1.08);
 
}
.iconClicked p {
  color: white;
}
.iconClicked i {
  color: limegreen;
}
</style>

