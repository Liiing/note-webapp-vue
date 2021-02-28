<template>
  <article class="message is-primary">
    <div class="message-header" @click="onTitleClick">
      <template v-if="isTitleEditable">
        <input type="text" :value="data.title" ref="titleInput" @blur="onTitleBlur" @input="$emit('onNoteAttributeChange', {value:$event.target.value, attribute:'title', uuid:data.uuid})">
      </template>
      <template v-else>
        <p>{{data.title}}</p>
      </template>
      <button class="delete" aria-label="delete" @click="$emit('onNoteDelete', data.uuid)"></button>
    </div>
    <div class="message-body" @click="onContentClick">
      <template v-if="isContentEditable">
        <textarea :value="data.content" ref="contentInput" @blur="onContentBlur" @input="$emit('onNoteAttributeChange', {value:$event.target.value, attribute:'content', uuid:data.uuid})"/>
      </template>
      <template v-else>
        {{data.content}}
      </template>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    data: {type: Object},
  },
  methods: {
    onTitleClick() {
      this.isTitleEditable = true;
      this.$nextTick(() => this.$refs.titleInput.focus());
    },
    onContentClick() {
      this.isContentEditable = true;
      this.$nextTick(() => this.$refs.contentInput.focus());
    },
    onTitleBlur() {
      this.isTitleEditable = false;
    },
    onContentBlur() {
      this.isContentEditable = false;
    }

  },
  data() {
    return {
      isTitleEditable: false,
      isContentEditable: false,
    }
  },
}
</script>

<style>
</style>
