<template>
<div class="toAbout">
  <transition name="fade">
    <div v-if="about" class="aboutMessage">
      <div @click="toAbout()"><span>click</span>☞About DJ List</div>
      <i class="el-icon-close" @click="deleteAbout"></i>
    </div>
  </transition>
</div>
</template>

<script>
export default {
  name: 'toAbout',
  data() {
    return {}
  },
  props: {
    'about': Boolean,
    'deleteAbout': Function
  },
  methods: {
    toAbout() {
      this.$router.push('/about')
    }
  },
}
</script>

<style lang="scss">
@mixin highlight() {
    content: '';
    width: 50px;
    height: 50px;
    // 非表示
    // background: linear-gradient(90deg, transparent, rgba(#fff, 1) 50%, transparent);
    position: relative;
    transform: rotate(135deg) skew(calc((90deg - 5deg) / 2), calc((90deg - 5deg) / 2));
}

@mixin exborder($color:#fff) {
    // 上
    text-shadow: 2px 2px 0 $color, -2px 2px 0 $color, 2px -2px 0 $color, -2px -2px 0 $color;
    // 下
    text-shadow: 2px 2px 2px $color, -2px 2px 2px $color, 2px -2px 2px $color, -2px -2px 2px $color;
}

.toAbout {
    cursor: pointer;
    animation: updown 2s linear infinite;

    @keyframes updown {
        0% {
            transform: translateY(0px);
        }

        50% {
            transform: translateY(10px);
        }

        100% {
            transform: translateY(0px);
        }
    }

    .aboutMessage {
        padding: 20px 10px;
        border: 1px solid rgba(#fff, .3);
        display: flex;
        // font
        font-size: 24px;
        color: #a458ec;
        font-weight: bold;
        font-family: "nicomojiPlus";
        @include exborder(#fff);
        line-height: 1;
        // background: #602f8e;
        background: linear-gradient(0deg, rgba(#fff, .8), transparent 50%, rgba(#fff, .8));
        margin: 0 20px 40px;
        border-radius: 1em;
        box-shadow: 5px 5px 20px 1px rgba(0,0,0,0.4);

        &::before {
            @include highlight();
            top: -4.5vh;
            left: 15vw;
        }

        &::after {
            @include highlight();
            bottom: -4.5vh;
            left: -58vw;
        }

        div {
            margin: 10px auto;
            display: flex;

            span {
                height: 12px;
                font-size: 12px;
                margin-top: 2.6px;
                font-weight: bold;
            }
        }

        i {
            display: flex;
            cursor: pointer;

            &::before {
                margin: auto;
                font-weight: bold;
            }
        }
    }
}

@media screen and (min-width:768px) {
    .toAbout {
        width: 100%;
        display: flex;

        .aboutMessage {
            width: 76%;
            margin: auto;
        }
    }
}

@media screen and (max-width:450px) {
    .toAbout {

        .aboutMessage {
            font-size: 18px;

            div {
                margin-top: 15px;
                width: 100%;
            }
        }
    }
}

@media screen and (max-width:370px) {
    .toAbout {

        .aboutMessage {
            font-size: 14px;
            padding: 15px 10px;

            div {
                margin-top: 17px;
            }
        }
    }
}
</style>
