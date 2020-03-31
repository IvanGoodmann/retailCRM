<template>
    <div class="field-box"
         :class="{'field-box__dirty': active}"
    >
        <div class="field-box__label"
             @click="toggle()"
        >
            {{ selectLabel }}
        </div>
        <div class="field-box__input"
             @click="toggle()"
        >
            {{selected}}
        </div>
        <div class="field-box__arrow"
             :class="{'active': opened}"
        ></div>
        <transition name="grow">
            <div class="field-box__list"
                 v-if="opened"
            >
                <div class="field-box__list-item"
                     v-for="(country, i) in choices"
                     :key="i"
                     @click="makeSelection(country.label)"
                >
                    {{country.label}}
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
  export default {
    name: "customSelect",
    props: ['choices', 'selectLabel'],
    data: () => ({
      selected: 'Российская федерация',
      opened: false,
      active: true
    }),
    methods: {
      toggle() {
        this.opened = !this.opened;
        this.active = true
      },
      makeSelection(selected) {
        this.selected = selected;
        this.opened = false;
      }
    },
    computed: {
    }
  }
</script>

<style lang="scss" scoped>
    $color-white: #ffffff;
    $color-grey: #6C6C6C;
    $color-text: #BBBBBB;
    $color-beige: #C0965C;
    $color-beige-hover: #c06c3d;
    $color-access: #89CC1B;
    $color-error: #e50d00;
    $menu-bg: #1C1C1B;
    $bg-black: #000000;
    $bg-input: #191919;
    $bg-input-focus: #333333;
    .field-box {
        $b: &;
        position: relative;
        margin-bottom: 20px;

        &__dirty {
            #{$b}__label {
                top: 20px;
                font-size: 14px;
            }
        }

        &__label {
            display: block;
            position: absolute;
            left: 30px;
            top: 50%;
            font-size: 20px;
            color: $color-grey;
            transform: translateY(-50%);
            transition: all 400ms ease;
        }

        &__input {
            box-sizing: border-box;
            width: 100%;
            font-size: 20px;
            color: $color-white;
            padding: 31px 30px 30px;
            outline: none;
            border: none;
            cursor: pointer;
            border-radius: 10px;
            background: $bg-input;

            &:focus {
                background: $bg-input-focus;
            }
        }

        &__arrow {
            position: absolute;
            right: 30px;
            top: 40%;
            width: 15px;
            height: 15px;
            border: 3px solid $color-grey;
            border-top-color: transparent;
            border-left-color: transparent;
            transform: rotate(45deg) translateY(-50%);
            transition: all 400ms ease;
            &.active {
                top: 50%;
                border: 3px solid $color-grey;
                border-bottom-color: transparent;
                border-right-color: transparent;
            }
        }
    }

    .select-box {
        position: relative;
    }

    .field-box__list {
        position: absolute;
        z-index: 99;
        overflow: hidden;
        width: 100%;
        margin-top: 5px;
        border-radius: 10px;
        background: $bg-input-focus;
        transition: all 400ms ease;

        &-item {
            font-size: 20px;
            color: $color-white;
            cursor: pointer;
            padding: 15px 30px;
            transition: all 400ms ease;

            &:hover {
                background: $color-text;
            }
        }
    }
    .grow-enter, .grow-leave-to {
        transform: scaleY(0);
        transform-origin: top;

    }
    .grow-enter-active, .grow-leave-active {
        transition: transform .4s;
        transform-origin: top;
    }
</style>
