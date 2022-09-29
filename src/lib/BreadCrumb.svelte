<script>
    import { Link, Router} from "svelte-routing";

    let currenUrl;
    function checkCurrentUrl(linkUrl) {
        currenUrl = window.location.href;
        if (currenUrl.includes("/category/")&&(linkUrl=="category")) {
            return "is-activate";
        } else if (currenUrl.includes("/search")&&(linkUrl=="search")) {
            return "";
        } else if ((linkUrl=="home") && (currenUrl.split("/").length <=4)){
            return "is-activate";
        } else {
            return ""
        }
    }
</script>

<nav class="breadcrumb is-centered" aria-label="breadcrumbs">
    <Router>
    <ul>
      <li class="{checkCurrentUrl("home")}"><Link to="/">主页</Link></li>
      <li class="{checkCurrentUrl("search")}"><Link to="/search">搜索</Link></li>
      <li class="{checkCurrentUrl("category")}"><Link to="/category/All">分类索引</Link></li>
    </ul>
</Router>
</nav>
