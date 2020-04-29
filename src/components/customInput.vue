<template>
    <div class="field-box"
         :class="{'field-box__dirty': dirty}"
    >
        <label
            class="field-box__label"
            @click="onClick()"
        >
            {{ label }}
        </label>
        <input
            ref="input"
            class="field-box__input"
            @focus="onFocus()"
            @blur="onBlur()"
            :type="type"
            :name="name"
            v-model="data"
        >
        <div class="field-box__valid">
<!--            <div class="field-box__valid-access"></div>-->
<!--            <div class="field-box__valid-error"></div>-->
        </div>
    </div>
</template>

<script>

  export default {
    name: "customInput",
    props: ['label', 'type', 'name', ],
    data: () => ({
      data: '',
      dirty: false,
    }),
    methods: {
      onClick() {
        this.$refs['input'].focus();
      },
      onFocus() {
        this.dirty = true;
      },
      onBlur() {
        this.data !== '' ? this.dirty = true : this.dirty = false;
      },
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
        border-radius: 10px;
        background: $bg-input;
        &:focus {
            background: $bg-input-focus;
        }
    }
    &__valid {
        position: absolute;
        right: -40px;
        top: 50%;
        transform: translateY(-50%);
        &-access {
            width: 10px;
            height: 15px;
            border: 3px solid $color-access;
            border-top-color: transparent;
            border-left-color: transparent;
            transform: rotate(45deg);
            transition: all 400ms ease;
        }
        &-error {
            position: relative;
            width: 20px;
            height: 20px;
            border: 3px solid $color-error;
            border-radius: 50%;
            transition: all 400ms ease;
            &:before, &:after {
                content: "";
                position: absolute;
                top: 2px;
                left: 50%;
                width: 3px;
                height: 80%;
                background: $color-error;
            }
            &:before {
                transform: translateX(-50%) rotate(45deg);
            }
            &:after {
                transform: translateX(-50%) rotate(-45deg);
            }
        }
    }
}
</style>
