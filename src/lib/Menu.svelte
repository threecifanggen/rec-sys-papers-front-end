<script>
    import {categories} from "../store/data";

    import { Router, Link, Route } from "svelte-routing";
</script>
<aside class="menu column is-one-quarter">
    <Router>
    <p class="menu-label">
      General
    </p>
    <ul class="menu-list">
      <li><Link to="/">Main</Link></li>
      <li><Link to="/">Search</Link></li>
    </ul>
    <p class="menu-label">
      分类索引
    </p>
    <ul class="menu-list">
        {#each categories as cat}
            <li><Link to="category/{cat}">{cat}</Link></li>
        {/each}
    </ul>
    </Router>
  </aside>