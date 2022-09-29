<!-- 分页功能 -->
<script>
    import EllipsisPageButton from "./EllipsisPageButton.svelte";
    import PageButton from "./pagination/PageButton.svelte";
    import { pageNowStore } from "../store/pageNowStore";

    export let itemNum = 100;
    export let itemNumPerPage = 10;
    let pageNow;

    
    pageNowStore.subscribe(value => {
		  pageNow = value;
	  });

    $: pageNum = Math.ceil(itemNum / itemNumPerPage);

    function clickPage(n, pageNum) {
        document.body.scrollIntoView();
        n = ((n >= 1)&&(n<=pageNum))? n: 1;
        pageNowStore.set(n);
        pageNowStore.subscribe(value => {
		      pageNow = value;
	      });
    };

    $: {
      console.log(pageNow);
    }
</script>

<nav class="pagination" aria-label="pagination">
    <div class="pagination-previous" on:click={clickPage(pageNow-1, pageNum)}>Previous</div>
    <div class="pagination-next" on:click={clickPage(pageNow+1, pageNum)}>Next page</div>

    <ul class="pagination-list">
    {#if pageNum <= 5 }
        {#each Array.from(Array(pageNum).keys()) as pageI}
            <PageButton pageI={pageI+1}></PageButton>
        {/each}
    {:else}
          {#if pageNow <= 2}
            <PageButton pageI={1}></PageButton>
            <PageButton pageI={2}></PageButton>
            <PageButton pageI={3}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum}></PageButton>
         {:else if pageNow >= pageNum - 2}
            <PageButton pageI={1}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum-2} ></PageButton>
            <PageButton pageI={pageNum-1}></PageButton>
            <PageButton pageI={pageNum}></PageButton>
         {:else}
            <PageButton pageI={1}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNow-1}></PageButton>
            <PageButton pageI={pageNow}></PageButton>
            <PageButton pageI={pageNow+1}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum}></PageButton>
        {/if}
    {/if}
</ul>
</nav>