<script>
  import { createEventDispatcher } from "svelte";
  import { Link, Route, Router } from "svelte-routing";
  import First from "./first.svelte";
  import Type from "./type.svelte";
  import Pg from "./Pg.svelte";
  import Shop from "./shop.svelte";
  import Login from "./login.svelte";
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    list-style: none;
    text-decoration: none;
  }
  .wrap {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  header {
    width: 100%;
    height: 50px;
    line-height: 50px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    text-align: center;
    background:#e43130;
    position: sticky;
    left:0;
    top:0;
    color:#fff;
    font-size: 14px;
  
  }
  header input {
    height: 40px;
    line-height: 40px;
    width: 80%;
    padding: 0 20px;
    border-radius: 20px;
   outline: none;
  }
  section {
    flex: 1;
    overflow: auto;
  }
  footer {
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-top: 1px solid #eee;
  }
  footer ul {
    display: flex;
    width: 100%;
  }
  footer ul li {
    flex: 1;
    text-align: center;
    align-items: center;
  }


</style>

<div class="wrap">

  <Router>
    <header>

      <span>更多</span>
      <input type="text" placeholder="请输入你想要的内容" />
      <span>登录</span>
    </header>
    <section>
      <Route path="First">
        <First />
      </Route>
      <Route path="Type">
        <Type />
      </Route>
      <Route path="Pg">
        <Pg />
      </Route>
      <Route path="Shop">
        <Shop />
      </Route>
      <Route path="Login">
        <Login />
      </Route>
    </section>
    <footer>
      <ul>
        <li>
          <Link to="/First">首页</Link>
        </li>
        <li>
          <Link to="/Type">分类</Link>
        </li>
        <li>
          <Link to="/Pg">拼购</Link>
        </li>
        <li>
          <Link to="/Shop">购物车</Link>
        </li>
        <li>
          <Link to="/Login">未登录</Link>
        </li>

      </ul>
    </footer>
  </Router>
</div>
