<template>
    <div id="app">
        <div class="wrap text-center">
            <h1>Vue Typeahead</h1>
            <p>Simple VueJS 2 TypeAhead component builded with Fetch Browser API.</p>
            <Typeahead
                source="https://jsonplaceholder.typicode.com/posts"
                place-holder="Type something"
                filter-key="title"
                :start-at="2"
            />
        </div>
    </div>
</template>

<script>
import Typeahead from './components/Typeahead'

export default {
    name: 'App',
    components: {
        Typeahead
    }
}
</script>

<style>
body {
    margin: 0;
    padding: 0;
    font-family: 'Open Sans', Arial, sans-serif;
    box-sizing: border-box;
    background: linear-gradient(135deg, #41B883 0%,#354953 100%);
    background-size: cover;
    min-height: 100vh;
    color: #fff;
}

h1 {
    font-size: 6vw;
}

h1, h2, h3, h4 {
    margin: 0; padding: 0;
    font-family: 'American Typewriter', Arial, sans-serif;
}

.text-center {
    text-align: center;
}

.wrap {
    max-width: 60vw;
    margin: 15vh auto;
}

/* #app {
    font-family: 'Muli', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    max-width: 900px;
    margin: 60px auto;
} */
</style>
