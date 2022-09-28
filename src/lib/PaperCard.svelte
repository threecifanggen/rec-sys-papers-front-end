<script>
    export let name = "Example PDF Name";
    export let url = "https://download.me.com";
    export let tagArray = ["test", "test1"];
    export let category = "Rank";
    export let year = "2003";
    export let authorArray = ["Huang Baochen", "Tang Mengjie"]
    export let company = "Aliyeye";
</script>

<div class="card are-fullwidth">
    <div class="card-content">
        <div class="content">
            <p><a href="{url}"><strong>{name}</strong></a></p>
            <br>
            <div class="tags"><strong>标签</strong>：
                {#each tagArray as tag}
                    <span class="tag is-info">#{tag}</span>
                {/each}
            </div>
            <p><strong>类目</strong>: {category}</p>
            <p style="text-align:right">
                {#each authorArray as author}
                    {author};&nbsp
                {/each}
            </p>
            <p style="text-align: right;"><a href="#/">{company}</a>, <time datetime="{year}">{year}</time></p>
        </div>
    </div>
</div>