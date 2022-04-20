<template>
  <div>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link
      rel="preload"
      href="fonts/roboto-bold.woff2"
      as="font"
      type="font/woff2"
      crossorigin="anonymous"
    />
    <link
      rel="preload"
      href="fonts/roboto-regular.woff2"
      as="font"
      type="font/woff2"
      crossorigin="anonymous"
    />
    <link
      rel="preload"
      href="fonts/roboto-light.woff2"
      as="font"
      type="font/woff2"
      crossorigin="anonymous"
    />
    <link
      rel="preload"
      href="fonts/roboto-bold.woff"
      as="font"
      type="font/woff"
      crossorigin="anonymous"
    />
    <link
      rel="preload"
      href="fonts/roboto-regular.woff"
      as="font"
      type="font/woff"
      crossorigin="anonymous"
    />
    <link
      rel="preload"
      href="fonts/roboto-light.woff"
      as="font"
      type="font/woff"
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="css/style.min.css" />
    <title>V!U!E! Pizza - главная</title>
    <header class="header">
      <div class="header__logo">
        <a href="index.html" class="logo">
          <img
            src="../assets/img/logo.svg"
            alt="V!U!E! Pizza logo"
            width="90"
            height="40"
          />
        </a>
      </div>
      <div class="header__cart">
        <a href="cart.html">0 ₽</a>
      </div>
      <div class="header__user">
        <a href="#" class="header__login"><span>Войти</span></a>
      </div>
    </header>

    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>

          <div class="content__dough">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите тесто</h2>

              <div class="sheet__content dough">
                <label
                  class="dough__input"
                  :class="[
                    `dough__input--${doughItem.id === 1 ? 'light' : 'large'}`,
                  ]"
                  v-for="doughItem of Pizza.dough"
                  :key="doughItem.id"
                >
                  <input
                    v-model="dough"
                    type="radio"
                    name="dought"
                    class="visually-hidden"
                    :value="doughItem"
                  />
                  <b>
                    {{ doughItem.name }}
                  </b>
                  <span>{{ doughItem.description }}</span>
                </label>
              </div>
            </div>
          </div>

          <div class="content__diameter">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите размер</h2>

              <div class="sheet__content diameter">
                <label
                  class="diameter__input"
                  v-for="size of Pizza.sizes"
                  :key="size.id"
                  :class="`diameter__input--${diameterPizzaSize[size.id]}`"
                >
                  <input
                    type="radio"
                    name="diameter"
                    value="small"
                    class="visually-hidden"
                  />
                  <span>
                    {{ size.name }}
                  </span>
                </label>
              </div>
            </div>
          </div>

          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">
                Выберите ингредиенты
              </h2>

              <div class="sheet__content ingredients">
                <div class="ingredients__sauce">
                  <p>Основной соус:</p>

                  <label
                    class="radio ingredients__input"
                    v-for="sauceItem of Pizza.sauces"
                    :key="sauceItem.id"
                  >
                    <input
                      v-model="sauces"
                      type="radio"
                      name="sauce"
                      :value="sauceItem"
                    />
                    <span>{{ sauceItem.name }}</span>
                  </label>
                </div>

                <div class="ingredients__filling">
                  <p>Начинка:</p>
                  <ul class="ingredients__list">
                    <li
                      class="ingredients__item"
                      v-for="ingredient of Pizza.ingredients"
                      :key="ingredient.id"
                    >
                      <span
                        class="filling"
                        :class="`filling--${fillingIngredient[ingredient.id]}`"
                      >
                        {{ ingredient.name }}
                      </span>

                      <div class="counter counter--orange ingredients__counter">
                        <button
                          type="button"
                          class="counter__button counter__button--minus"
                          disabled
                        >
                          <span class="visually-hidden">Меньше</span>
                        </button>
                        <input
                          type="text"
                          name="counter"
                          class="counter__input"
                          value="0"
                        />
                        <button
                          type="button"
                          class="counter__button counter__button--plus"
                        >
                          <span class="visually-hidden">Больше</span>
                        </button>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input
                type="text"
                name="pizza_name"
                placeholder="Введите название пиццы"
              />
            </label>

            <div class="content__constructor">
              <div
                class="pizza"
                :class="[`pizza--foundation--${foundationDough}-${saucePizza}`]"
              >
                <div class="pizza__wrapper">
                  <div class="pizza__filling pizza__filling--ananas"></div>
                  <div class="pizza__filling pizza__filling--bacon"></div>
                  <div class="pizza__filling pizza__filling--cheddar"></div>
                </div>
              </div>
            </div>

            <div class="content__result">
              <p>Итого: 0 ₽</p>
              <button type="button" class="button" disabled>Готовьте!</button>
            </div>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import Misc from "../static/misc.json";
import Pizza from "../static/pizza.json";
export default {
  data() {
    return {
      Misc,
      Pizza,
      dough: Pizza.dough[1],
      sauces: Pizza.sauces[1],
      diameterPizzaSize: {
        1: "small",
        2: "normal",
        3: "big",
      },
      fillingIngredient: {
        1: "mushrooms",
        2: "cheddar",
        3: "salami",
        4: "ham",
        5: "ananas",
        6: "bacon",
        7: "onion",
        8: "chile",
        9: "jalapeno",
        10: "olives",
        11: "tomatoes",
        12: "salmon",
        13: "mozzarella",
        14: "parmesan",
        15: "blue_cheese",
      },
    };
  },
  computed: {
    foundationDough() {
      return this.dough.id === 1 ? "small" : "big";
    },
    saucePizza() {
      return this.sauces.id === 1 ? "tomato" : "creamy";
    },
  },
};
</script>

<style scoped></style>
