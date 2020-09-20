<template>
  <section class="contributions">
    <h3>
      Une page se tourne, on te souhaite bonne chance pour cette nouvelle qui commence !
    </h3>
    <div class="don" v-for="contribution in contributions" :key="contribution.id">
      <p>{{ contribution.text }}</p>
      <img :src="contribution.img" alt="" />
    </div>
  </section>
</template>

<script>
export default {
  name: "Contributions",
  data() {
    return {
      contributions: [
        {
          id: 0,
          img: require(`@/assets/icon/maple-syrup.svg`),
          text: "Isabelle t'offre du sirop d'érable !",
        },
        {
          id: 1,
          img: require(`@/assets/icon/moose.svg`),
          text: "Thomas t'offre un caribou !",
        },
        {
          id: 2,
          img: require(`@/assets/icon/hockey-equipment.svg`),
          text: "Marine t'offre un jersey de hockey !",
        },
        {
          id: 3,
          img: require(`@/assets/icon/poutine.svg`),
          text: "Joseph t'offre une poutine !",
        },
        {
          id: 4,
          img: require(`@/assets/icon/hat.svg`),
          text: "Malik t'offre un chapeau de ranger !",
        },
        {
          id: 5,
          img: require(`@/assets/icon/bonnet.svg`),
          text: "Audrey F. t'offre un bonnet !",
        },

        {
          id: 6,
          img: require(`@/assets/icon/hockey-cross.svg`),
          text: "Annette t'offre une crosse de hockey !",
        },
        {
          id: 7,
          img: require(`@/assets/icon/mitts.svg`),
          text: "Loïc t'offre des moufles !",
        },
        {
          id: 8,
          img: require(`@/assets/icon/totem.svg`),
          text: "Léonore t'offre un totem !",
        },
        {
          id: 9,
          img: require(`@/assets/icon/teepee.svg`),
          text: "Arthur t'offre un teepee !",
        },
        {
          id: 10,
          img: require(`@/assets/icon/beer.svg`),
          text: "Audrey D. t'offre une bière !",
        },
        {
          id: 11,
          img: require(`@/assets/icon/beaver.svg`),
          text: "Frédéric t'offre un castor !",
        },
      ],
    };
  },
};
</script>

<style>
.contributions {
  max-width: 85%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: center;
  margin: 0 auto;
}
.contributions h3 {
  width: 100;
  font-weight: 500;
  line-height: 1.3;
  margin-top: 0;
}
.don {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 45%;
  margin: 5px 0;
}
.don p {
  margin: 0;
}
.don img {
  width: 50px;
  height: 50px;
}

@media screen and (max-width: 600px) {
  .don {
    width: 100%;
    margin: 10px 0;
  }
  .don p {
    font-size: 0.85em;
  }
  .don img {
    padding-left: 10px;
  }
}
</style>
