<script>
	import { onMount } from 'svelte';

	let t;
	const TIME_ENTRIES_KEY = 'timeEntries';
	const ESTIMATED_TIME_KEY = 'estimatedTime';

	function formatTime(totalMinutes) {
		const hours = Math.floor(totalMinutes / 60);
		const minutes = totalMinutes % 60;

		if (hours === 0) {
			return `${minutes} min`;
		} else if (minutes === 0) {
			return `${hours} godz`;
		} else {
			return `${hours} godz ${minutes} min`;
		}
	}

	onMount(() => {
		const today = new Date();
		const oneMonthAgo = new Date();
		oneMonthAgo.setMonth(today.getMonth() - 1);
	});
</script>
<div style="padding: 1rem;">

	<div style="display: flex; gap: 1rem; align-items: center; margin-bottom: 2rem;">
		<label for="date-from">Od daty:</label>
		<input id="date-from" style="margin: 8px 4px 0 0" type="date">

		<label for="date-to">Do daty:</label>
		<input id="date-to" style="margin: 8px 4px 0 0" type="date">

		<button id="filter-button">Filtruj</button>
	</div>

	<div>
		<div style="margin-bottom: 2rem;">
			<h3 style="font-size: 1.3em">Łączny czas dla tablicy:</h3>
			<p id="board-total-time">Ładowanie...</p>
		</div>
		<div style="margin-bottom: 2rem;">
			<h3 style="font-size: 1.3em">Raporty czasu według list:</h3>
			<div id="list-time-reports" style="margin-left: 1rem;">Ładowanie...</div>
		</div>
		<div style="margin-bottom: 2rem;">
			<h3 style="font-size: 1.3em">Raporty czasu według kart:</h3>
			<div id="card-time-reports" style="margin-left: 1rem;">Ładowanie...</div>
		</div>
		<div style="display: flex; gap: 1rem; justify-content: flex-end; margin-bottom: 2rem;">
			<button
			" id="export-board-button">Eksportuj do CSV</button>
			<button id="close-button">Zamknij</button>
		</div>
	</div>
</div>