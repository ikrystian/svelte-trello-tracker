<script>
	import { onMount } from 'svelte';
	
	let trelloClient;
	
	onMount(() => {
		const script = document.createElement('script');
		script.src = 'https://p.trellocdn.com/power-up.min.js';
		script.onload = () => {
		trelloClient = window.TrelloPowerUp;
		initPowerUp();
		};
		document.head.appendChild(script);
	});
	
	function initPowerUp() {
		if (!trelloClient) return;
		
		trelloClient.initialize({
			'board-buttons': function(t) {
				return [{
				icon: {
					dark: 'https://img.icons8.com/ios-filled/50/000000/clock--v1.png',
					light: 'https://img.icons8.com/ios-filled/50/ffffff/clock--v1.png'
				},
				text: 'Raporty czasu',
				callback: function(t) {
					return t.modal({
					title: 'Raporty czasu dla całej tablicy',
					url: './time-report',
					height: 500
					});
				}
				}];
			},
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
