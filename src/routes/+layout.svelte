<script>
	import { onMount } from 'svelte';
	
	let trelloClient;
	
	onMount(() => {
		const script = document.createElement('script');
		script.src = 'https://p.trellocdn.com/power-up.min.js';
		script.onload = () => {
		trelloClient = window.TrelloPowerUp;
		// Initialize your Power-Up when script is loaded
		initPowerUp();
		};
		document.head.appendChild(script);
	});
	
	function initPowerUp() {
		if (!trelloClient) return;
		
		trelloClient.initialize({
		'card-buttons': function(t, options) {
			return [{
			icon: '/icon.svg',
			text: 'My Button',
			callback: function(t) {
				return t.modal({
				url: '/card-modal',
				height: 500
				});
			}
			}];
		}
		// Add other capabilities here
		});
	}
	import '../app.css';
	let { children } = $props();
</script>

{@render children()}
