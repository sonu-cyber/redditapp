<template>
	<div class="subreddit">
		<a :href="makeUrl(item.data.permalink)" :style ="makeImage(item.data.thumbnail)" target='_blank' class='thumbnail'>
		</a>

		<div class="details">
		  <a :href="makeUrl(item.data.permalink)" :title='item.data.title' target='_blank' class='title'>
		    {{ item.data.title | truncate }}
		  </a>
			<div class="name">
			<i class="material-icons">name</i>
				{{ item.data.name }}
			</div>
			<br/>
		  <div class="stats">
		    <i class="material-icons">thumbs_up_down</i>
		      {{ item.data.score }}
		    <i class="material-icons">forum</i>
		   	  {{ item.data.num_comments }}
		  </div>
	  </div>
  </div>
</template>

<script>
	//passing in the item from the Subreddits component
	export default {
		name:"subreddit",
		props: ["item"],
		methods: {
   	  makeImage: function(img){
     	  return 'background-image: url('+img+')';
  		},
  		makeUrl: function(permalink) {
  		  return "https://www.reddit.com" + permalink;
  		}
	  },
	  filters: {
	    truncate: function(value){
	      var length=50;
	    	if (value.length <= length){
	    	  return length;
	    	} else {
	    		return value.substring(0, length) + '...';
	    	}
	    }
	  }
  }
</script>
<style>
  .subreddit{
    display:flex;
  }
  .thumbnail{
    display: block;
    flex:0 0 65px;
    height: 65px;
    background-repeat:no-repeat;
    background-size: cover;
    background-position: center;
    margin-right: 12px;
		margin-bottom:20px;
    border-radius: 5px;
		border:1px solid coral;
   }
   .subreddit .details .title {
   	font-size: 15px;
   	margin-bottom: 5px;
   	color:#ddd;
		background-color: #62de6e;
	 }
	 .subreddit .details .name {
	 	display:flex;
		justify-content: flex-start;
	 	font-size: 15px;
		margin-botton: 5px;
		background-color:#e8d4d4;
		color:#03a9f4;
	 }
   .subreddit .stats {
     font-size: 12px;
     margin-right: 4px;
     margin-top: 7px;
     display:inline-block;
		 color:#fff;
     background-color: #e8a593;
   }
   .subreddit .stats i {
   	font-size: 10px;
   	margin-right: 2px;
   }
</style>
