<script>
    import {Router,Link,Route} from "svelte-routing";
    import App from "./App.svelte";
    import Home from "./Home.svelte";
</script>
<div>
    <Router>
        <Link to="App">app</Link>
        <Link to="/home">home</Link>
        <Route path="app">
            <App />                                       
        </Route>
        <Route path="home/*" component={Home}>
        
        </Route>
    </Router>
</div>