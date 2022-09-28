<script>
    import EllipsisPageButton from "./EllipsisPageButton.svelte";
    import PageButton from "./PageButton.svelte";

    export let itemNum = 100;
    export let itemNumPerPage = 10;
    export let pageNow = 10;

    $: pageNum = Math.ceil(itemNum / itemNumPerPage);

    function clickPage(n) {
        pageNow = n;
    };
    
    function checkNow(pageI, pageNow) {
      return (pageI + 1 == pageNow)? "is-current":""
    }

    $: {
      console.log(pageNow);
    }
</script>

<nav class="pagination" aria-label="pagination">
    <div class="pagination-previous" on:Click={clickPage(pageNow-1)}>Previous</div>
    <div class="pagination-next" on:Click={clickPage(pageNow+1)}>Next page</div>

    <ul class="pagination-list">
    {#if pageNum <= 5 }
        {#each Array.from(Array(pageNum).keys()) as pageI}
            <PageButton pageI={pageI+1} pageNow={pageNow}></PageButton>
        {/each}
    {:else}
          {#if pageNow <= 2}
            <PageButton pageI={1} pageNow={pageNow}></PageButton>
            <PageButton pageI={2} pageNow={pageNow}></PageButton>
            <PageButton pageI={3} pageNow={pageNow}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum} pageNow={pageNow}></PageButton>
         {:else if pageNow >= pageNum - 3}
            <PageButton pageI={1} pageNow={pageNow}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum-2} pageNow={pageNow}></PageButton>
            <PageButton pageI={pageNum-1} pageNow={pageNow}></PageButton>
            <PageButton pageI={pageNum} pageNow={pageNow}></PageButton>
         {:else}
            <PageButton pageI={1} pageNow={pageNow}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum-1} pageNow={pageNow}></PageButton>
            <PageButton pageI={pageNum} pageNow={pageNow}></PageButton>
            <PageButton pageI={pageNum+1} pageNow={pageNow}></PageButton>
            <EllipsisPageButton></EllipsisPageButton>
            <PageButton pageI={pageNum} pageNow={pageNow}></PageButton>
        {/if}
    {/if}
</ul>
</nav>