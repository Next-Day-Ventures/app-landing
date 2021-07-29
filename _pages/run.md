---
layout: page
title: Run
include_in_header: false
---
<h1 id='title'>Run</h1>
<h2 id='subtitle'></h2>
<div>Please open the <a href="/">SameRun</a> app for more information.</div>
<img alt='Author Profile' id='author' style="
  width:100px;
  height:100px;
  object-fit:cover;
  border-radius:50%;
"/>
<div>Starting <span id='planned_start'></span>, until about <span id='planned_end'></span></div>
<div>Estimated km: <span id='distance'></span></div>
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
    var description = params.description.replace(/\+/g, " ");
    if (description == "undefined") description = 'This run does not have a description.';
    document.getElementById("title").innerHTML = params.title.replace(/\+/g, " ");
    document.getElementById("subtitle").innerHTML = description;
    document.getElementById("author").src = params.picture;
    document.getElementById("planned_start").innerHTML = params.planned_datetime.replace(/\+/g, " ").substr(0, 16);
    document.getElementById("planned_end").innerHTML = params.planned_end.replace(/\+/g, " ").substr(0, 16);
    document.getElementById("distance").innerHTML = params.distance;
    document.getElementById("lang").innerHTML = params.language_icon.replace(/\+/g, " ");
</script>