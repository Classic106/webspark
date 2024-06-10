<template>
  <div class="head center">
    <div class="head_row">
      <img class="head_logo" src="@/assets/Group 1.png" alt="logo" />
      <div class="head_main center">
        <div class="head_head center">
          <h2 class="head_title">monblanproject</h2>
          <button class="head_button">Start on 17-02-2016</button>
        </div>
        <div class="head_info center">
          <p class="info_p">
            <span>{{ numberWithCommas(posts) }}</span> posts
          </p>
          <p class="info_p">
            <span>{{ numberWithCommas(followers) }}</span> followers
          </p>
          <p class="info_p">
            <span>{{ numberWithCommas(following) }}</span> following
          </p>
        </div>
        <div class="head_picker">
          <span class="head_date">Date</span>
          <div class="pickers">
            <Datepicker v-model="from" />
            <Datepicker v-model="to" />
          </div>
        </div>
      </div>
    </div>
    <div class="first"></div>
  </div>
</template>

<script setup>
import Datepicker from "vue3-datepicker";
import { ref } from "vue";
const from = ref(new Date());
const to = ref(new Date());
</script>

<script>
import { numberWithCommas } from "@/utils/functions";

export default {
  name: "HeadComponent",
  data: () => ({
    posts: 870,
    followers: 11787,
    following: 112,
  }),
  methods: {
    numberWithCommas,
  },
};
</script>

<style lang="scss" scoped>
.head {
  min-height: 10.75rem;
  display: flex;
  position: relative;
  background: #ffffffab;

  .head_row {
    display: flex;
    width: 50%;
    justify-content: start;

    .head_logo {
      width: 8.625rem;
      height: 8.625rem;
      margin-right: 5.375rem;
      cursor: pointer;
    }
  }

  .head_main {
    flex-direction: column;

    .head_head {
      .head_title {
        font-family: Montserrat;
        font-size: 1.5rem;
        font-weight: 500;
        line-height: 1.829rem;
        letter-spacing: -0.01em;
        text-align: left;
        margin-right: 1rem;
      }

      .head_button {
        color: #3d8eda;
        background-color: inherit;
        cursor: pointer;
        height: 1.75rem;
        border-radius: 2px;
        border: 1px solid #3d8eda;
      }
    }

    .head_info {
      .info_p {
        font-size: 0.875rem;
        margin-right: 1.5rem;

        span {
          font-weight: bold;
        }
      }
    }
    .head_picker {
      display: flex;
      width: 100%;
      justify-content: space-between;

      .pickers {
        display: flex;
        flex-direction: row;

        div:nth-child(1) {
          margin-right: 1rem;
        }
      }

      .head_date {
        font-size: 1rem;
        margin-right: 0.688rem;
      }
    }
  }
}

.first {
  position: absolute;
  background: url("@/assets/Vector\ 1.svg");
  background-repeat: no-repeat;
  min-height: 100vh;
  min-width: 100%;
  left: 0;
  top: 0;
  z-index: -1;
}

@media screen and (max-width: 600px) {
  .head {
    .head_row {
      width: 100%;
      justify-content: space-around;

      .head_logo {
        align-self: center;
        margin-right: 1.375rem;
      }
    }

    .head_picker {
      .pickers {
        flex-direction: column !important;
        margin-bottom: 0.5rem;

        div:nth-child(1) {
          margin-right: 0rem;
          margin-bottom: 0.5rem;
        }
      }
    }
  }
}

@media screen and (max-width: 400px) {
  .head {
    margin: 0 0.5rem;

    .head_row {
      .head_logo {
        margin-right: 0.5rem;
      }
    }
  }
}
</style>
