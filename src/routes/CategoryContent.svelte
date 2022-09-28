<script>
    import CardPagination from "../lib/CardPagination.svelte";
    import Menu from "../lib/Menu.svelte";
    import PaperCard from "../lib/PaperCard.svelte";
    import papers from "../store/data.json";
    import { pageNowStore } from "../store/pageNowStore";

    const itemNumPerPage = 10;
    let pageNow;

    pageNowStore.subscribe(value => {
		  pageNow = value;
	});

    export let cat = "All";
    $: selectedPaper = (cat == "All") ? papers: (papers.filter((p) => p.category== cat));
    $: selectedItemNum = selectedPaper.length;
    $: showPaper = selectedPaper.slice(itemNumPerPage * (pageNow - 1), itemNumPerPage * pageNow);
</script>

<div>
<article>
    {#each showPaper as paper}
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
    itemNum={selectedItemNum}
    itemNumPerPage={itemNumPerPage}
    />
</div>
