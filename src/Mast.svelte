<script type="text/javascript">
	import SearchArea from './SearchArea.svelte'
	import Notification from './Notification.svelte'

	let error = false
	let search_term;
	let response

	const fetchLyrics = (term) => {
		if (term == null) {
			error = true
		} else {
			let lyrics_data = {
				title : "",
				cover : ""
			}
			const apiURL = 'https://api.lyrics.ovh/suggest/'+term;

			const res = fetch(apiURL).then(function result(res) {
				response = res.json()

				response.then( res => {
				response = res.data

				for (var i = response.length - 1; i >= 0; i--) {
					const lyricURL = 'https://api.lyrics.ovh/v1/'+response.artist.name+'/'+response.title

					const lyric_res = fetch(lyricURL).then(result => {
						console.log(result.json())
					})
				}
				
				
			})

			})


		}
		error = false
	}

	const submit = (e) => {
		e.preventDefault()
		fetchLyrics(search_term)
	}
</script>

<div class="container">
	{#if error}
		<Notification />
	{/if}

	<form class="form-inline" on:submit = {submit}>
	  <div class="form-group mx-sm-3 mb-2 col-sm-9">
	    <input type="text" class="form-control col-sm-12" id="inputPassword2" placeholder="Mind is a prison" bind:value={search_term}>
	  </div>
	  <button type="submit" class="btn btn-primary mb-2">Search</button>
	</form>


{#if response == undefined} <h3>No lyrics available</h3>
{:else}
<div class="accordion" id="accordionExample">
	{#each response as lyric, key}
		<SearchArea cover = {lyric.album.cover} title = {lyric.title} key = {key} lyrics = {lyric.title}/>
	{/each}
</div>

{/if}
</div>
<style type="text/css">
	.container{
		margin-top: 5em;
	}
	.center{
		text-align: center;
	}
	h3{
		text-align: center;
	}
</style>