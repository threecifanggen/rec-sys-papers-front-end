<script>
    
    export let pageNow;
    export let pageI;
    function checkNow(pageI, pageNow) {
        return (pageI == pageNow)? "is-current":""
    }
</script>

<li>
<div class="pagination-link {checkNow(pageI, pageNow)}" aria-label="Goto page {pageI}">{pageI}</div></li>