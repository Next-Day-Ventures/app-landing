---
layout: page
title: Run
include_in_header: false
---
<h1 id='title'>Run</h1>
<h2 id='subtitle'></h2>
<script>
    function getSearchParameters() {
        var prmstr = window.location.search.substr(1);
        return prmstr != null && prmstr != "" ? transformToAssocArray(prmstr) : {};
    }
    function transformToAssocArray( prmstr ) {
        var params = {};
        var prmarr = prmstr.split("&");
        for ( var i = 0; i < prmarr.length; i++) {
            var tmparr = prmarr[i].split("=");
            params[tmparr[0]] = tmparr[1];
        }
        return params;
    }
    var params = getSearchParameters();
    document.getElementById("title").innerHTML = params.title;
    document.getElementById("subtitle").innerHTML = params.description;
</script>