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
    <h1>Trello Time Tracker</h1>
    <p>To jest rozszerzenie do raportowania czasu spędzonego nad zadaniami w Trello.</p>
</div>