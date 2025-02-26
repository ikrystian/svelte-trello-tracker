<!-- src/routes/card-modal/+page.svelte -->
<script>
  import { onMount } from 'svelte';
  let t;
  
  onMount(() => {
    if (window.TrelloPowerUp) {
      t = window.TrelloPowerUp.iframe();
      
      // Example: getting card data in the modal
      t.card('all')
        .then(function(card) {
          // Use card data
          console.log(card);
        });
    }
  });
  
  function closeModal() {
    if (t) {
      t.closeModal();
    }
  }
</script>

<div class="modal-content">
  <h2>Card Modal</h2>
  <button on:click={closeModal}>Close</button>
</div>