<script>
	import { currentUser } from '$lib/pocketbase';
</script>

{#if $currentUser}
	<div class="flex justify-center">
		<!-- The button to open modal -->
		<label for="my_modal_7" class="btn btn-primary">open modal</label>

		<!-- Put this part before </body> tag -->
		<input type="checkbox" id="my_modal_7" class="modal-toggle" />
		<div class="modal" role="dialog">
			<div class="modal-box">
				<h3 class="text-lg font-bold">Create post!</h3>
			</div>
			<label class="modal-backdrop" for="my_modal_7">Close</label>
		</div>
	</div>
{/if}
