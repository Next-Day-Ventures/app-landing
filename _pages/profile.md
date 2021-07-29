---
layout: page
title: Profile
include_in_header: false
---
<h1 id='nickname'>User Profile</h1>
<h3 id='profile_bio'></h3>
<div>Please open the <a href="/">SameRun</a> app for more information.</div>
<img alt='Profile Image' id='image' style="
  width:100px;
  height:100px;
  object-fit:cover;
  border-radius:50%;
"/>

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
    document.getElementById("nickname").innerHTML = params.nickname.replace(/\+/g, " ");
    document.getElementById("profile_bio").innerHTML = params.profile_bio.replace(/\+/g, " ");
    document.getElementById("image").src = params.picture;
</script>