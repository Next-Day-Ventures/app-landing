---
layout: page
title: Run
include_in_header: false
---
<h1 id='title'>Run</h1>
<h2 id='subtitle'></h2>
<div>Please open the SameRun app for more information.</div>
<img alt='Author Profile' id='author' height='200px'/>
<div id='planned_start'></div>
<div><span id='distance'></span>km</div>
<div>Languages: <span id='lang'></span></div>

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
            params[tmparr[0]] = decodeURIComponent(tmparr[1]);
        }
        return params;
    }
    var params = getSearchParameters();
    document.getElementById("title").innerHTML = params.title.replace(/\+/g, " ");
    document.getElementById("subtitle").innerHTML = params.description.replace(/\+/g, " ");
    document.getElementById("author").src = params.picture;
    document.getElementById("planned_start").innerHTML = params.planned_datetime;
    document.getElementById("distance").innerHTML = params.distance;
    document.getElementById("lang").innerHTML = params.language_icon;
</script>