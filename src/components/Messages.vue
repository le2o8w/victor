<template>
  <section>
    <div class="message" v-for="message in messages" :key="message.id">
      <!-- Quote left -->
      <svg
        class="top"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        width="116"
        height="104"
        viewBox="0 0 116 104"
      >
        <g transform="translate(7 -19.844)">
          <path
            d="M0,72.092v42.857H42.857V72.092H14.286A28.6,28.6,0,0,1,42.857,43.521V29.235A42.9,42.9,0,0,0,0,72.092Z"
            transform="translate(0 0)"
          />
          <path
            d="M276.739,43.521V29.235a42.9,42.9,0,0,0-42.857,42.857v42.857h42.857V72.092H248.168a28.6,28.6,0,0,1,28.571-28.571Z"
            transform="translate(-176.739 0)"
          />
        </g>
      </svg>
      <!-- Message -->
      <div class="text">
        <p v-html="message.text"></p>
        <span class="signature">{{ message.name }}</span>
      </div>
      <!-- Quote right -->
      <svg
        class="bottom"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        width="116"
        height="104"
        viewBox="0 0 116 104"
      >
        <g transform="translate(107 124.341) rotate(180)">
          <path
            d="M0,72.092v42.857H42.857V72.092H14.286A28.6,28.6,0,0,1,42.857,43.521V29.235A42.9,42.9,0,0,0,0,72.092Z"
            transform="translate(0 0)"
          />
          <path
            d="M276.739,43.521V29.235a42.9,42.9,0,0,0-42.857,42.857v42.857h42.857V72.092H248.168a28.6,28.6,0,0,1,28.571-28.571Z"
            transform="translate(-176.739 0)"
          />
        </g>
      </svg>
    </div>
    <div class="message">
      <Contributions />
    </div>
    <!-- Retour accueil -->
    <div class="return">
      <a @click="endOfMessages">Rejouer le diaporama</a>
    </div>
  </section>
</template>

<script>
import Contributions from "./Contributions.vue";

export default {
  name: "Messages",
  components: {
    Contributions,
  },
  data() {
    return {
      messages: [
        {
          id: 0,
          name: "Arthur",
          text: "Je savais que tu était pas la pour être ici. Bonne continuation et plein de réussites (ie. putes & bagnoles).",
        },
        {
          id: 1,
          name: "Malik",
          text: "L'héritage du PingMyBoss que tu nous as laissé représente pour nous la clé de la réussite !",
        },
        {
          id: 2,
          name: "Audrey F.",
          text:
            "Quelques mois de décalage mais ton beau projet va enfin aboutir. Je suis vraiment contente pour toi. Les projets de messagerie doivent te paraître loin déjà (comme pour moi 😉). Profites bien de cette nouvelle aventure perso et pro. Bises.",
        },
        {
          id: 3,
          name: "Thomas",
          text:
            "Bon départ au pays où la poutine coule à flot. Tu as oublié de léguer ton appli la plus importante : le pingeur automatique de Phillipe ! Je continuerai à coder avec le cul pour perpétuer la tradition.",
        },
        {
          id: 4,
          name: "Audrey D.",
          text:
            "Je te souhaite un bon départ au pays des caribou ! Tu vas bien te cailler mais ce sera un super dépaysement.  Amuse toi bien dans ton nouveau job et fais pleins de belles rencontres !",
        },
        {
          id: 5,
          name: "Marine",
          text: "Bonne continuation Victor et n’oublie pas ta doudoune!",
        },
        {
          id: 6,
          name: "Léonore",
          text:
            "C'était cool de travailler avec toi ! Je te souhaite de belles rencontres, des nouveaux projets passionnants et de ne pas glisser sur une plaque de verglas en sortant de chez toi... Eclate-toi bien dans cette nouvelle aventure !",
        },
        {
          id: 7,
          name: "Joseph",
          text: "Je te souhaites des bonnes parties de tennis clavier et de bonnes séances de gainage après les poutines!!! Et surtout \"RENTRES CHEZ TOI!!!!\". Nota fais pas comme moi qui ai écrasé un raton laveur le premier soir.",
        },
        {
          id: 8,
          name: "Isabelle, Fred, Annette et Loïc",
          text: "Bonne continuation Victor !",
        },
      ],
    };
  },
  methods: {
    endOfMessages() {
      this.$emit("endOfMessages", true);
    },
  },
};
</script>

<style>
.message {
  position: relative;
  max-width: 80%;
  margin: 1.25rem auto;
  background: #750606;
  border-radius: 0.3125rem;
  padding: 1.875rem 0;
  box-shadow: 0 0.1875rem 0.375rem rgba(0, 0, 0, 0.16), 0 0.1875rem 0.375rem rgba(0, 0, 0, 0.23);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.message:hover {
  box-shadow: 0 0.875rem 1.75rem rgba(0, 0, 0, 0.25), 0 0.625rem 0.625rem rgba(0, 0, 0, 0.22);
}

.text {
  width: 85%;
  margin: 0 auto;
}
p {
  line-height: 1.6;
  margin-bottom: 0;
}
.signature {
  display: block;
  text-align: right;
  font-family: "Kumbh Sans", Arial, sans-serif;
  font-variant-caps: all-petite-caps;
  letter-spacing: 0.0625rem;
  font-size: 1.5em;
  padding-right: 0.625rem;
}

svg {
  width: 1.875rem;
  height: 1.5625rem;
  fill: #fff;
}
svg.top {
  position: absolute;
  left: 0.9375rem;
  top: 0.9375rem;
}

svg.bottom {
  position: absolute;
  right: 0.9375rem;
  bottom: 0.9375rem;
}
.return {
  max-width: 80%;
  margin: 1.25rem auto;
  display: flex;
  justify-content: flex-end;
}
.return a {
  display: block;
  cursor: pointer;
  background: #750606;
  border-radius: 0.3125rem;
  padding: 0.9375rem 1.25rem;
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}
.return a:hover {
  box-shadow: 0 0.1875rem 0.375rem rgba(0, 0, 0, 0.16), 0 0.1875rem 0.375rem rgba(0, 0, 0, 0.23);
}

@media screen and (max-width: 50rem) {
  svg {
    width: 1.25rem;
    height: 0.9375rem;
  }
  .signature {
    margin-bottom: 0.625rem;
  }
  .return a {
    width: 100%;
    text-align: center;
  }
}
</style>
