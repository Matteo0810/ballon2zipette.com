<template>
  <div role="banner">
    <div class = "content" style="--time:20s">
      <div>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
      </div>
      <div>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
        <span>❄️🎄Distribution <b>GRATUITE</b> de Pago-Flash à la chiche de noël ❄️🎄</span>
      </div>

    </div>

  </div>

  <div class="hero-header">
    <img alt="pago-flash" src="/images/pago-flash/pago-flash.svg" />
    <h1>Pago Flash</h1>
    <h2>Le flash éphémère pour tous vos évènements</h2>
  </div>

  <section>
    <article class="about-us">
      <div>
        <div>
          <h2>Un savoir-faire</h2>
          <p>Les pago-flash sont préparés avec amour dans les meilleurs
            quartier de Lannion. La <b>vodka</b>, le <b>rhum</b>, le <b>whisky</b> et le <b>ricard</b>
            viennent des meilleures coins du monde.</p>
        </div>
        <div>
          <h2>Des partenaires de renom</h2>
          <p>Nos partenaires fournissent les meilleurs flash de toute la région. Nasdas, Samos, Assia, mettent un point d'honneur à fournir les meilleurs ballons pour aller avec le bon flash, comme du vin quoi.</p>
        </div>
      </div>
      <img src="/images/pago-flash/savoir-faire.jpg" alt="Pago flash savoir faire" />
    </article>

    <article class="partenaires">
      <h2>Nos fournisseurs</h2>

      <ul>
        <li>
          <img src="/images/pago-flash/partenaires/momoplansnap.jpg" alt="momoplansnap" />
        </li>
        <li>
          <img src="/images/pago-flash/partenaires/ballon2zipette.jpg" alt="ballon2zipette" />
        </li>
        <li>
          <img src="/images/pago-flash/partenaires/planBraquage.jpg" alt="planBraquage" />
        </li>
      </ul>
    </article>

    <article class="selection">
      <h2>Notre offres</h2>
      <div><span id = "codepromo">Code promo : BALLON66 | -66% sur l'ensemble de nos offres</span></div>
      <section>
        <article v-for="offer in offers" :key="offer">
          <h4 v-if="offer.popular">Populaire</h4>
          <img :src="'images/pago-flash/thumbnails/'+offer.thumbnail+'.png'" :alt="offer.title" />
          <h3>{{ offer.title }}</h3>

          <footer>
            <div class="quantity-selector">
              <button @click="offer.quantity > 0 && offer.quantity--" :disabled="offer.quantity < 1">-</button>
              <span>{{ offer.quantity }}</span>
              <button @click="offer.quantity++">+</button>
            </div>


          </footer>
        </article>
      </section>
      <button class="commander" @click="commander" v-if="totalQuantity > 0">Commander x{{ totalQuantity }}</button>
      <div>
        <div class="ordered" v-if="orderedCheck && totalQuantity > 0">
            <label for="nom">Nom :</label>
            <input type="text" id="nom" name="nom" required>

            <label for="prenom">Prénom :</label>
            <input type="text" id="prenom" name="prenom" required>

            <input type="submit" value="Envoyer">
      </div>
      </div>

    </article>

    <div class="telegram">
      <h2>Rejoins le télégram maintenant</h2>
      <h4>Si tu ne rejoins pas samos viendra dans tes rêves.</h4>

      <img src="/images/telegram-link.jpeg" alt="telegram link" />
      <span><a target="_blank" href="https://t.me/+ZSKuml6mYhNmZTU0">Ou via le lien</a></span>

      <footer>
      </footer>
    </div>

    <h5>Contact : assiasamosbraquageforsure@ballon2zipette.com</h5>
  </section>
</template>

<script setup>
import { ref, onMounted, computed,watch } from 'vue'

onMounted(() => {
  document.title = "Pago-flash éphémère | Ballon22ipette.com";
});

const offers = ref([
  {
    thumbnail: "pack-1",
    title: "VodKH + 3 ballons OFFERTS",
    popular: true,
    quantity: 0
  },
  {
    thumbnail: "pack-2",
    title: "Whisky-flash + formation CRYPTO",
    quantity: 0
  },
  {
    thumbnail: "vodka",
    title: "VodKH",
    quantity: 0
  },
  {
    thumbnail: "whisky",
    title: "Whisky-flash",
    quantity: 0
  }
]);
const orderedCheck = ref(false);
const totalQuantity = computed(() => {
  return offers.value.reduce((a, b) => {
    return a + b.quantity;
  }, 0);
});

function commander() {
  if (totalQuantity.value > 0) {
    orderedCheck.value = true;
  }
}

// Surveiller totalQuantity pour réinitialiser orderedCheck si nécessaire [CHATGPT]
watch(totalQuantity, (newVal) => {
  if (newVal === 0) {
    orderedCheck.value = false;
  }
});

</script>l

<style scoped>
  @keyframes changeColor {
    0% { background-color: var(--orange); }
    25% { background-color: var(--green); }
    50% { background-color: var(--yellow); }
    75% { background-color: var(--red); }
    100% { background-color:var(--blue); }
  }
  @keyframes scroll {
    0% {
        transform: translateX(100%);
    }

    100% {
        transform: translateX(-100%);
    }
}

@keyframes scroll2 {
    0% {
        transform: translateX(0);
    }

    100% {
        transform: translateX(-200%);
    }
}

  .commander {
      display: block;
      width: fit-content;
      color: var(--black);
      font-size: 1.4em;
      background-color: var(--orange);
      border-radius: 0.3em;
      cursor: pointer;
      padding: 10px 20px;
      border: none;
      margin: auto auto 20px;
  }

  div.hero-header {
    margin: auto;
    width: fit-content;
    height: calc(100vh - 10vh);

    text-align: center;

    font-size: 1.4em;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    &>h1 {
      font-family: "poppins-bold", sans-serif;
    }
  }

  div[role="banner"] {
    background-color: var(--orange);
    padding: 1em .8em;
    gap : 0px;
    font-size: 30px;
    overflow: hidden;
    &>div.content{
      overflow: hidden;
      width: max-content;
      display: flex;
      gap:20px;
      &>div{
        min-width: 200px;
        animation: scroll var(--time) linear infinite;
        animation-delay: calc(var(--time) * -1);

        white-space: nowrap;
        &>span{
          overflow: hidden;
          white-space: nowrap;
          color : var(--black);
        }
      }

      &>div:nth-child(2){
        animation: scroll2 var(--time) linear infinite;
        animation-delay: calc(var(--time) / -2);
      }
    }

  }

  section {
    &>article.about-us {
      display: flex;
      flex-wrap: wrap;
      gap: 5em;

      justify-content: center;

      &>div {
        display: flex;
        justify-content: space-around;
        flex-direction: column;

        &>div {
          width: 30em;

          &>h2 {
            margin-bottom: .5em;
          }
          &>p {
            text-align: justify;
          }
        }
      }
      &>img {
        width: 15em;
        border-radius: 10px;
      }
    }
    &>article.partenaires {
      &>ul {
        display: flex;
        justify-content: center;
        gap: 2em;
        flex-wrap: wrap;
        list-style: none;

        &>li {
          &>img {
            border-radius: 10px;
            width: 15em;
          }
        }
      }
    }

    &>article.partenaires,
    &>article.selection {
      margin-top: 5em;
      &>h2 {
        text-align: center;
        margin-bottom: 1em;
      }
      &>div{
        display: flex;
        justify-content: center;
        &>span{
          background-color: var(--orange);
          color: var(--black);
          width: fit-content;
          border-radius: 0.3em;
          padding: 5px  20px  5px  20px;
          cursor: pointer;
        }
        &>span:hover {
          animation: changeColor 1s infinite;
        }

      }


      &>section {
        display: flex;
        gap: 1em;
        justify-content: center;
        flex-wrap: wrap;
        margin: 3em 0;

        &>article {
          background-color: var(--black-2);
          flex-basis: 10em;

          border-radius: 15px;
          text-align: center;
          position: relative;
          padding: 1em 2em 4em;

          &>h4 {
            position: absolute;
            top: -23px;
            left: 50%;

            transform: translateX(-50%);

            background-color: var(--orange);
            color: var(--black);

            padding: .5em .8em;
            border-radius: 100px;
          }

          &>img {
            width: 15em;
            height: 15em;
            margin-bottom: .5em;
          }

          &>h3 {
            font-family: "poppins-bold", sans-serif;
          }

          &>footer {
            margin-top: .5em;
            position: absolute;
            left: 0;
            bottom: 10px;
            width: 100%;

            &>div.quantity-selector {
              display: flex;
              align-items: center;
              gap: 1em;
              justify-content: center;

              &>button {
                padding: .5em .8em;
                background-color: var(--black);
                color: white;

                border: 1px solid var(--gray-1);
                border-radius: 5px;
                cursor: pointer;
                font-size: 1em;
                transition: all .5s ease;

                &:disabled {
                  opacity: .5;
                  cursor: unset;
                }

                &:not(:disabled):hover {
                  background-color: var(--black-2);
                }
              }
            }
          }
        }

      }
      &>div{
        &>div.ordered{
          background:  var(--black-2);
          border-radius: 40px;
          display: flex;
          align-items: center;
          justify-content: center;
          vertical-align: center;
          height: 5em;
          gap:20px;
          width: 50em;
          &>label{
            display: block;
          }
          input[type="text"] {
            padding: 0.5em;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 1em;
          }
          input[type="submit"] {
            padding: 0.7em;
            border: none;
            border-radius: 4px;
            background: var(--orange);
            color: var(--black);
            font-size: 1em;
            cursor: pointer;

          }
          input[type="submit"]:hover {
            animation: changeColor 1s infinite;
          }
        }
      }


    }



    &>div.telegram{
      margin-top: 100px;
      display: flex;
      flex-direction: column;
      text-align: center;
      align-items: center;
      gap : 1em;

      &>img{

        width: 10em;
      }

      &>span{
        background-color: var(--orange);
        color: var(--black);
        width: fit-content;
        border-radius: 0.3em;
        padding: 5px  20px  5px  20px;
        cursor: pointer;
      }

    }

    h5 {
          text-align: center;
          margin-bottom: 1em;
      }
  }

  /* RESPONSIVE */
  @media screen and (max-width: 520px) {
    section>article.about-us>div>div {
      width: unset;
      padding: 0 1em;
    }
  }

</style>
