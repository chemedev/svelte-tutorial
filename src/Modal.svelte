<script>
  export let message = 'default value';
  export let isPromo = false;
  let showModal = true;
</script>

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background-color: #ffffff;
  }
  .promo .modal {
    background-color: crimson;
    color: #ffffff;
  }
</style>

{#if showModal}
  <div class="backdrop" class:promo={isPromo}>
    <div class="modal">
      <p>{message}</p>
    </div>
  </div>
{/if}
