<script type="text/javascript">
	import SearchArea from './SearchArea.svelte'
	import Notification from './Notification.svelte'

	let error = false
	let search_term;
	let response

	const fetchLyrics = (term) => {
		if (search_term.length == 0) {
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

				const lyricURL = 'https://api.lyrics.ovh/v1/'+artist+'/'+song

				const lyric_res = fetch(lyricURL).then(result => {
				
			})
				
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

<div class="bx--tile container">
	{#if error}
		<Notification />
	{/if}
	<form on:submit = {submit} >
	  <div data-search role="search" class="bx--search bx--search--lg">
	    <label id="search-input-label-1" class="bx--label" for="search__input-1">Search</label>
	    <input class="bx--search-input" type="text" id="search__input-1" placeholder="MInd is a Prison" bind:value={search_term}>
	    <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" class="bx--search-magnifier" width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><path d="M15,14.3L10.7,10c1.9-2.3,1.6-5.8-0.7-7.7S4.2,0.7,2.3,3S0.7,8.8,3,10.7c2,1.7,5,1.7,7,0l4.3,4.3L15,14.3z M2,6.5	C2,4,4,2,6.5,2S11,4,11,6.5S9,11,6.5,11S2,9,2,6.5z"></path></svg>
	    <button class="bx--search-close bx--search-close--hidden" title="Clear search
	        input" aria-label="Clear search input">
	      
	      <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" class="bx--search-clear" width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><path d="M12 4.7L11.3 4 8 7.3 4.7 4 4 4.7 7.3 8 4 11.3 4.7 12 8 8.7 11.3 12 12 11.3 8.7 8z"></path></svg>
	      
	    </button>
	  </div>
	  <div class="example-button-wrapper center">
	    <button class=" bx--btn bx--btn--primary bx--btn--field"  type="submit">
	      Search
	    </button>
	  </div>
  </form>
</div>
{#if response == undefined} <h3>No lyrics available</h3>
{:else}
<div class="bx--tile">
<ul data-accordion class="bx--accordion">
	{#each response as lyric, key}
		<SearchArea cover = {lyric.album.cover} title = {lyric.title} key = {key}/>
	{/each}
</ul>
</div>

{/if}

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