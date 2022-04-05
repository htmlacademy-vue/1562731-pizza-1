<template>
  <!DOCTYPE html>
  <html lang="ru">
    <head>
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
    </head>
    <body>
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
                    class="dough__input dough__input--light"
                    v-for="dough of Pizza.dough"
                    :key="dough.id"
                  >
                    <input
                      type="radio"
                      name="dought"
                      value="light"
                      class="visually-hidden"
                      checked
                    />
                    <b>
                      {{ dough.name }}
                      <img :src="dough.image" class="dough__input-img" alt="" />
                    </b>
                    <span>{{ dough.description }}</span>
                  </label>
                </div>
              </div>
            </div>

            <div class="content__diameter">
              <div class="sheet">
                <h2 class="title title--small sheet__title">Выберите размер</h2>

                <div class="sheet__content diameter">
                  <label
                    class="diameter__input diameter__input--big"
                    v-for="size of Pizza.sizes"
                    :key="size.id"
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
                      v-for="sauce of Pizza.sauces"
                      :key="sauce.id"
                    >
                      <input type="radio" name="sauce" value="tomato" checked />
                      <span>{{ sauce.name }}</span>
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
                        <span class="filling">
                          <img
                            :src="ingredient.image"
                            alt=""
                            class="filling__img-ingredient"
                          />
                          {{ ingredient.name }}
                        </span>

                        <div
                          class="counter counter--orange ingredients__counter"
                        >
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
                <div class="pizza pizza--foundation--big-tomato">
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
    </body>
  </html>
</template>

<script>
import Misc from "../static/misc.json";
import Pizza from "../static/pizza.json";
export default {
  data() {
    return {
      Misc,
      Pizza,
    };
  },
};
</script>

<style scoped>
.filling__img-ingredient {
  position: absolute;
  top: 50%;
  left: 0;
  transform: translate(0, -50%);
  display: block;
  width: 32px;
  height: 32px;
  content: "";
  border-radius: 50%;
  background-color: #ffffff;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 80% 80%;
}
.dough__input-img {
  position: absolute;
  top: 50%;
  left: 0;
  transform: translate(0, -50%);
  width: 36 px;
  height: 36 px;
  content: "";
  transition: 0.3s;
  border-radius: 50%;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
</style>
