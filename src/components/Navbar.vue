<template>
  <div class="container">
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="https://bulma.io">
          <img
            src="https://bulma.io/images/bulma-logo.png"
            width="112"
            height="28"
          />
        </a>
      </div>

      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-end">
          <a class="button is-primary" @click="$emit('onNoteAdd')">
            <strong>+</strong>
          </a>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
</script>

<style>
</style>
