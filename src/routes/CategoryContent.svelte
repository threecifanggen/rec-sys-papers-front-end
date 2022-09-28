<script>
    import CardPagination from "../lib/CardPagination.svelte";
    import Menu from "../lib/Menu.svelte";
    import PaperCard from "../lib/PaperCard.svelte";
    import papers from "../store/data.json";

    export let cat = "All";
    $: selectedPaper = (cat == "All") ? papers: (papers.filter((p) => p.category== cat));
</script>

<div>
<article>
    {#each selectedPaper as paper}
       <PaperCard 
        year={paper.year}
        url={paper.url}
        tagArray = {paper.tag}
        name={paper.name}
        authorArray = {paper.authors}
        company = {paper.company} 
        />
        <br>
        <br>
    {/each}
</article>

<CardPagination 
    itemNum=100
    itemNumPerPage=10
    pageNow=2/>
</div>
