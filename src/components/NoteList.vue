<template>
  <transition-group name="note" tag="div" class="container">
    <template v-for="note in data" :key="note.uuid">
      <Note class="note" :data="note" @onNoteDelete="$emit('onNoteDelete', $event)" @onNoteAttributeChange="$emit('onNoteAttributeChange', $event)"/>
    </template>
  </transition-group>
</template>

<script>
import Note from './Note'

export default {
  components: {
    Note,
  },
  props: {
    data: {type: Array, default: () => []},
  }
}

</script>

<style lang="scss">
  .note {
    height: 100px;
    overflow: hidden;
    transition: all 0.3s ease-out;

    &-enter-from {
      opacity: 0;
      transform: translateY(30px);
    }

    &-leave-to {
      animation: leave 0.3s ease-out;
    }
  }

  @keyframes leave {
    50% {
      height: 100px;
      opacity: 0;
      transform: translateX(30px);
    }
    100% {
      height: 0;
      opacity: 0;
      transform: translateX(30px);
    }
  }

  // .note {
  //   height: 100px;
  //   overflow: hidden;
  //   transition: all 0.3s ease-out;

  //   &-enter-from {
  //     opacity: 0;
  //     transform: translateY(30px);
  //   }

  //   &-leave-to {
  //     height: 0;
  //     margin-bottom: 0 !important;
  //     opacity: 0;
  //     transform: translateY(-30px);
  //   }
  // }
</style>
