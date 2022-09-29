<script>
    import CardPagination from "../lib/pagination/CardPagination.svelte";
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
    $: showPaperLeft = showPaper.slice(0, itemNumPerPage/2);
    $: showPaperRight = showPaper.slice(itemNumPerPage/2, itemNumPerPage)
</script>

<section class="section columns">
    <Menu />
    <section class="container is-three-quarters">
        <div class="columns">
        <div class="column is-half"><article>
            {#each showPaperLeft as paper}
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
        </article></div>

        <div class="column is-half"><article>
            {#each showPaperRight as paper}
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
        </article></div>
        </div>
        <div>
            <CardPagination 
                itemNum={selectedItemNum}
                itemNumPerPage={itemNumPerPage}/>
        </div>    
    </section>
    
</section>
