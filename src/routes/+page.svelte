<script>
  import { onMount } from 'svelte';
  
  onMount(() => {
    // Access the client from window if loaded in app.html
    if (window.TrelloPowerUp) {
      const t = window.TrelloPowerUp.iframe();
      
      // Example: Getting context information
      t.render(function() {
        t.card('id', 'name')
          .then(function(card) {
            // Use card data
            console.log(card);
          });
      });
    }
  });
</script>

<div class="power-up-content">
  <h1>My Trello Power-Up</h1>
  <!-- Your Power-Up content -->
</div>