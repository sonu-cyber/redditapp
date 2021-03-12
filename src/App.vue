<template>
  <div id="app">
    <header>
      <h3>Subreddits</h3>
    </header>
    <subreddits category="food"></subreddits>
    <subreddits category="adventofcode"></subreddits>
    <subreddits category="science"></subreddits>
    <subreddits category="space"></subreddits>
    <subreddits category="nasa"></subreddits>
    <subreddits category="movies"></subreddits>
  </div>
</template>

<script>
import subreddits from './components/Subreddits';
import subreddit from './components/Subreddit'


export default {
  name: 'App',
  components: {
    subreddits,
    subreddit
  }

}
</script>

<style>
  body {
    font-family: arial;
    background: #f4f4f4;
    color: #666666;
    margin: 0;
    padding: 0;
  }
   h3 {
    text-decoration:none;
    text-align: center;
   }
   header {
    background:lightcoral;
    padding:20px;
    color:#fff;
   }




</style>
