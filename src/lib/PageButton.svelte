<script>
    import { pageNowStore } from "../store/pageNowStore";

    let pageNow;
    export let pageI;
    
    function checkNow(pageI, pageNow) {
        return (pageI == pageNow)? "is-current":""
    }

    pageNowStore.subscribe(value => {
		  pageNow = value;
	});
    
    function clickPage(n) {
        pageNowStore.set(n);
        pageNowStore.subscribe(value => {
		  pageNow = value;
	    });
    };
</script>

<li>
<div class="pagination-link {checkNow(pageI, pageNow)}" aria-label="Goto page {pageI}" on:click="{clickPage(pageI)}">{pageI}</div></li>