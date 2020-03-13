<script type="text/javascript">
	export let cover = ""
	export let title = ""
	export let lyrics = ""
	export let key
</script>

  <div class="card">
    <div class="card-header" id="headingOne">
      <h2 class="mb-0">
      	<img src="{cover}" alt="Cover image">
        <button class="btn btn-link" type="button" data-toggle="collapse" data-target="#pane{key}" aria-expanded="true" aria-controls="collapseOne">
          {title}
        </button>
      </h2>
    </div>

    <div id="pane{key}" class="collapse" aria-labelledby="headingOne" data-parent="#accordionExample">
      <div class="card-body">
        {lyrics}
      </div>
    </div>
  </div>

<style type="text/css">
	img{
		height: 3em;
	}
</style>