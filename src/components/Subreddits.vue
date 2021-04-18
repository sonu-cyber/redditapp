<template>
  <div class="subreddits container">
  	<h3>{{ category | capitalize}}</h3>
  	<ul class="item-list">
      <li v-for='post in subreddits'>
    	<subreddit :item="post"></subreddit>
    	{{ post.data.title}}
      </li>
    </ul>
    <button class='btn btn-success btn-sm mybtn' @click='backtoTop()'>Back To Top</button>
  </div>
</template>

<script>
	import subreddit from './Subreddit'

	export default {
		name:'subreddits',
		props: ['category'],
		data() {
			return {
			    subreddits:[],
      }//return
    },//data()
    components: {
      subreddit
    },
    filters: {
      capitalize: function(value) {
        if (!value) return '';
        value = value.toString();
        return value.charAt(0).toUpperCase() + value.slice(1);
      }
    },
   methods:{
     backtoTop: function() {
       document.body.scrollTop = 0;
       document.documentElement.scrollTop = 0;
     }
   },
   created: function() {
     console.log('Created Ran..');
     this.$http.get("https://www.reddit.com/r/" + this.category + "/top.json?limit=5")
     .then((response) => {
      this.subreddits = response.data.data.children;
      console.log("response",response);
      console.log("response.data",response.data);
      console.log("response.data.data.children",response.data.data.children);
   }, error => {
      console.error(error);
   });//.then
   }//created
  }//export default
</script>
<style>
  .container {
  	max-width:600px;
  	font-family: Arial;
  	background:#fff;
    margin: 30px auto;
  	padding:20px;
    color:#666;
    border: 5px solid #218838;
    box-shadow:0 0 3px #ccc;
  }
  .subreddits {
  	min-width: 400px;
  	padding: 25px 45px;
  }
  .subreddits h3 {
  	font-size:20px;
  	margin-bottom: 10px;
  	margin-top:0;
    color:#333;
    border:none;
    box-shadow:0 0 3px #e6a1a1;
    transition:all 4s ease-in-out 2s;
  }
  .subreddits h3:hover {
    transform: scale(1.1);
    font-size: 34px;
    color:#ea685d;
  }
  .subreddits .item-list {
  	list-style:none;
  	padding-top:20px;
    padding-bottom:20px;
    border-top: 1px solid #ccc;
  }
  .subreddits .item-list li {
    padding-top:10px;
  	padding-bottom: 20px;
    font-size:14px;
  	color:#333;
  }
  .subreddits .mybtn {
    background-color: #ea685d;
    transition: all 4s ;
    transition-timing-function: ease-in-out 2s;
    transition-delay: 2s;
  }
  .subreddits .mybtn:hover {
    transform: scale(1.1);
    width:150px;
  }
  </style>
