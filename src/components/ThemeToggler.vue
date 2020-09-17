<template>
    <div class="toggler">
        <label class="toggler__label">
            <input
              type="checkbox"
              class="toggler__input"
              @change="toggleTheme">
            <span class="toggler__round"></span>
        </label>
    </div>
</template>

<script>
export default {
   props:['theme'],
   methods: {
     toggleTheme() {
       this.$emit('toggle-theme', !this.theme)
     }
   }
}
</script>

<style scoped lang='scss'>
  .toggler {
    &__label {
      position:relative;
      display:inline-block;
      width:60px;
      height:34px;
    }

    &__input {
      opacity:0;
      width:0;
      height:0;
      &:checked + .toggler__round {
        background: #E56464;
      }

      &:checked + .toggler__round:before {
          -webkit-transform:translateX(26px);
          -ms-transform: translateX(26px);
          transform:translateX(26px);
      }

      &:focus + .toggler__round {
        box-shadow: 0 0 2px #E56464;
      }
    }

    &__round {
      position:absolute;
      top:0;
      left:0;
      bottom: 0;
      right: 0;
      border-radius:36px;
      cursor: pointer;
      background-color: rgb(43,55,96);
      -webkit-transition: 0.4s;
      transition:0.4s;
      &:before {
        position: absolute;
        border-radius:50%;
        content:'';
        height:26px;
        width:26px;
        left:4px;
        bottom:4px;
        background-color:#fff;
        -webkit-transition: 0.4s;
        transition:0.4s;
      }
    }
  }
</style>