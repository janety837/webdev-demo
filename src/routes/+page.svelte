<script>
	import { currentUser, pb } from '$lib/pocketbase';

	let caption = '';
	const formData = new FormData();

	const handleFileChange = (event) => {
		for (let file of event?.target?.files) {
			formData.append('photo', file);
		}
	};

	const handleCreatePost = async () => {
		formData.append('caption', caption);
		formData.append('user', $currentUser?.id);
		//await pb.collection('posts').create(formData);
		caption = '';
	};
</script>

<!--{#if $currentUser}-->
<div class="flex justify-center">
	<!-- The button to open modal -->
	<label for="my_modal_7" class="btn btn-primary">open modal</label>

	<!-- Put this part before </body> tag -->
	<input type="checkbox" id="my_modal_7" class="modal-toggle" />
	<div class="modal" role="dialog">
		<div class="modal-box">
			<div class="space-y-4">
				<h3 class="text-lg font-bold">Create post</h3>
				<label class="form-control">
					<div class="label">
						<span class="label-text">Caption</span>
					</div>
					<textarea class="textarea textarea-bordered h-24" bind:value={caption} />
				</label>
				<input
					type="file"
					class="file-input file-input-bordered w-full max-w-xs"
					on:change={handleFileChange}
				/>
				<label for="my_modal_7" class="btn btn-primary btn-block" on:click={handleCreatePost}
					>create post</label
				>
			</div>
		</div>
		<label class="modal-backdrop" for="my_modal_7">Close</label>
	</div>
</div>
<!--{/if}-->
