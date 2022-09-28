<script>
    import PaperCard from "../lib/PaperCard.svelte";
    import papers from "../store/data.json";

    export let cat = "All";
    $: selectedPaper = (cat == "All") ? papers: (papers.filter((p) => p.category== cat));
</script>

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