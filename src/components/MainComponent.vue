<template>
  <div class="container center">
    <div class="main">
      <div class="main_head">
        <img
          class="blocks"
          :class="{ chosed: is_row === true }"
          src="@/assets/Group 13.png"
          alt="blocks"
          @click="is_row = false"
        />
        <img
          class="lines"
          :class="{ chosed: is_row === false }"
          src="@/assets/Group 13.png"
          alt="lines"
          @click="is_row = true"
        />
      </div>
      <ListItems :items="items" :is_row="is_row" />
    </div>
    <div class="center">
      <button class="load_more" @click="loadMore">LOAD MORE</button>
    </div>
    <div class="second"></div>
  </div>
</template>

<script>
import ListItems from "./ListItems";

export default {
  name: "MainComponent",
  components: { ListItems },
  data: () => ({
    is_row: true,
  }),
  setup() {
    const obj = {
      id: 0,
      name: "name",
      image: "Rectangle 20.png",
      activity: {
        today: {
          likes: 128,
          comments: 31,
        },
        "9-08-2016": {
          likes: 67,
          comments: 22,
        },
      },
      uploaded: "9-08-2016",
    };

    const items = [obj];

    for (let i = 1; i < 9; i++) {
      const newObj = { ...obj };
      newObj.image = `Rectangle 20 (${i}).png`;
      items.push(newObj);
    }

    return { items };
  },
  methods: {
    loadMore: function () {
      console.log("loadmore");
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  flex-direction: column;
  display: flex;
  position: relative;
}

.main {
  max-width: 52.25rem;
  width: 100%;

  .main_head {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin: 1.438rem 0;

    .blocks,
    .lines {
      cursor: pointer;
    }

    .blocks {
      margin-right: 1.688rem;
    }
  }
}

.load_more {
  height: 1.75rem;
  padding: 0.469rem 1.625rem;
  margin-top: 1.875rem;
  margin-bottom: 3.813rem;
  border-radius: 0.875rem;
  color: #929292;
  border: 1px solid #929292;
  font-family: Roboto;
  font-size: 0.688rem;
  font-weight: 500;
  line-height: 0.806rem;
  letter-spacing: -0.03em;
  background-color: inherit;
  cursor: pointer;
}

.chosed {
  filter: invert(49%) sepia(100%) saturate(1574%) hue-rotate(187deg)
    brightness(91%) contrast(86%);
}

.second {
  position: absolute;
  background: url("@/assets//Vector\ 2.svg");
  background-repeat: no-repeat;
  min-height: 22.6rem;
  min-width: 13.1rem;
  bottom: 0;
  right: 0;
  z-index: -1;
}

@media screen and (max-width: 800px) {
  .main {
    .main_head {
      margin: 1rem;
    }
  }
}
</style>
