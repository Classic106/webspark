<template>
  <div class="list center">
    <div class="list_body" :class="{ is_row }">
      <div
        class="list_body_item"
        :class="{ is_row }"
        v-for="item in items"
        :key="item.id"
      >
        <img :src="require(`@/assets/images/${item.image}`)" :alt="item.name" />
        <div class="list_body_info" :class="{ is_row }">
          <div class="info_today" :class="{ is_row }">
            <span>Today</span>
            <div>
              <div class="likes">
                <img src="@/assets/ci_heart-fill.png" :alt="item.name" />
                {{ item.activity.today.likes }}
              </div>
              <div class="comments">
                <img
                  src="@/assets/ic_round-mode-comment.png"
                  :alt="item.name"
                />
                {{ item.activity.today.comments }}
              </div>
            </div>
          </div>
          <div class="info_upload" :class="{ is_row }">
            <span>{{ item.uploaded }}</span>
            <div>
              <div class="likes">
                <img src="@/assets/ci_heart-fill.png" :alt="item.name" />
                {{ numberWithCommas(item.activity[item.uploaded].likes) }}
              </div>
              <div class="comments">
                <img
                  src="@/assets/ic_round-mode-comment.png"
                  :alt="item.name"
                />
                {{ numberWithCommas(item.activity[item.uploaded].comments) }}
              </div>
            </div>
          </div>
          <div class="info_uploaded" :class="{ is_row }">
            <span>Image upload</span> {{ item.uploaded }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { numberWithCommas } from "@/utils/functions";

export default {
  name: "ListItems",
  props: {
    items: {
      type: Array,
      default: () => [],
    },
    is_row: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    numberWithCommas,
  },
};
</script>

<style lang="scss" scoped>
.list {
  display: flex;
  flex-direction: column;

  .list_body {
    &.is_row {
      width: 100%;
    }

    &:not(.is_row) {
      flex-wrap: wrap;
      justify-content: space-around;
      display: flex;
    }

    .list_body_item {
      &:not(.is_row) {
        width: 24%;
        flex-direction: column;
      }

      min-height: 5.375rem;
      display: flex;
      margin-bottom: 0.5rem;
      background-color: #fff;

      img {
        object-fit: cover;
      }

      .list_body_info {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
        justify-content: space-between;

        &.is_row {
          width: 100%;
          margin: 0 1.875rem;
        }

        &:not(.is_row) {
          margin: 1rem;
        }

        span {
          font-weight: bold;
          font-family: Roboto;
          font-size: 1rem;
          font-weight: 500;
          line-height: 1.172rem;
        }

        .info_today,
        .info_upload,
        .info_uploaded {
          display: flex;
          flex-direction: column;
          align-items: flex-start;

          span {
            font-weight: bold;
            margin-bottom: 0.5rem;
          }

          div {
            display: flex;
            font-family: Roboto;
            font-size: 0.875rem;
            font-weight: 500;
            line-height: 1.026rem;

            .likes,
            .comments {
              img {
                height: 1.125rem;
                width: 1.125rem;
                margin-right: 0.375rem;
              }
            }

            .likes {
              margin-right: 1.125rem;
            }
          }
        }

        .info_today,
        .info_upload {
          &:not(.is_row) {
            div {
              flex-direction: column;

              .likes,
              .comments {
                flex-direction: row;
                margin-bottom: 0.5rem;
              }
            }
          }
        }

        .info_uploaded {
          &:not(.is_row) {
            margin-top: 0.5rem;
            width: 100%;
            flex-direction: row;
            justify-content: space-between;
          }
        }
      }
    }
  }
}

@media screen and (max-width: 800px) {
  .list {
    margin-left: 2rem;
    margin-right: 2rem;

    .list_body {
      .list_body_item {
        &:not(.is_row) {
          width: 32%;
        }

        .list_body_info {
          &.is_row {
            margin: 0 1rem;
          }
        }
      }
    }
  }
}

@media screen and (max-width: 400px) {
  .list {
    margin-left: 1rem;
    margin-right: 1rem;
  }

  .list {
    .list_body {
      .list_body_item {
        &:not(.is_row) {
          width: 49%;
        }

        .list_body_info {
          margin: 0.5rem;

          .info_today,
          .info_upload,
          .info_uploaded {
            div {
              flex-direction: column;
              align-items: center;
              width: 100%;

              img {
                margin-right: 0rem;
              }

              img:nth-child(2) {
                margin-left: 0rem;
              }

              .likes,
              .comments {
                margin-bottom: 0.5rem;
              }

              .likes {
                margin-right: 0rem;
              }
            }
          }
        }
      }
    }
  }
}
</style>
