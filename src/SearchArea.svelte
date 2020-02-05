<script type="text/javascript">
	export let cover = ""
	export let title = ""
	export let key
</script>

<li data-accordion-item class="bx--accordion__item">
  <button class="bx--accordion__heading" aria-expanded="false" aria-controls="pane{key}">
    <svg focusable="false" preserveAspectRatio="xMidYMid meet" style="will-change: transform;" xmlns="http://www.w3.org/2000/svg" class="bx--accordion__arrow" width="16" height="16" viewBox="0 0 16 16" aria-hidden="true"><path d="M11 8L6 13 5.3 12.3 9.6 8 5.3 3.7 6 3z"></path></svg>
    <div class="bx--accordion__title"><img src="{cover}" alt="Cover image"><h3>{title}</h3></div>
  </button>
  <div id="pane{key}" class="bx--accordion__content">
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna
      aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
  </div>
</li>

<style type="text/css">
	.bx--tile{
		margin-top: 1em;
	}
	.bx--accordion__content{
		text-align: center;
	}
	h3{
		line-height: 1em;
    	padding-left: 1em;
    	text-align: center;
    	margin: auto;
    	margin-left: 1em;
	}
	.bx--accordion__title{
		display: flex;
	}
</style>