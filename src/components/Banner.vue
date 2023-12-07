<script>
export default {
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
};
</script>

<template>
  <div class="card-section container py-5">
    <div class="card mx-3 mb-5 rounded-lg" v-for="(card, index) in cards" :key="index">
      <div class="card__image mb-3 rounded-lg"></div>
      <p class="card__description mb-3">{{ card.description }}</p>
			<button class="card__button rounded-pill px-4 py-2 mt-3">READ MORE</button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card-section {
	.card {
    background-color: #fff;
    padding: 25px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    border: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: auto;
    min-width: 350px;
    height: 600px;

		&__image {
      background-image: url('../assets/400x300.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: cover;
			width: 100%;
      min-height: 200px;
		}

    &__description {
      text-align: center;
      font-size: 1.3rem;
      height: 250px;
      font-weight: 500px;
    }

    &__button {
      border: 3px solid #000;
      font-weight: 900;
      letter-spacing: 2px;
      background-color: #fff;
      color: #000;
    }

    &__button:hover {
      border: 3px solid #fff;
      background-color: #000;
      color: #fff
    }
	}
}

@media (min-width: 1024px) {
  .card-section {
    display: flex;
    flex-direction: row;
    .card {
    }
  }
}
</style>