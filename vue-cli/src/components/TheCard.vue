<template>
  <div class="mycard">
    <b-card
      title="Card Title"
      img-src="https://picsum.photos/600/300/?image=25"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem"
      class="mb-2"
    >
      <b-card-text class="p3">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </b-card-text>

      <b-button v-b-modal.modal-2>Forgot Password</b-button>
    </b-card>

    <b-modal id="modal-2" title="BootstrapVue">
      <p class="my-4">Hello from modal 2!</p>
    </b-modal>
  </div>
</template>

<script>
export default {};
</script>

<style>
.mycard {
  background: #eef1f4;
}
</style>