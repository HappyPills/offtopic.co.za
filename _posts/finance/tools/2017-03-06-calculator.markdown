---
layout: post
title:  "Annualised Growth Calculator"
permalink: /finance/tools/annualised-growth-calculator/
date:   2017-03-06
tags:   finance tools
---

Read [this article](/finance/how-to-calculate-annualised-growth/) for information about what this calulator does.

### Fill out the details and GO!

<div class="list-group" id="input-group" style="width: 290px;">
  <div class="list-group-item">
    <label style="width:100px;">Start value:</label>
    <input type="number" value="1" id="startval" />
  </div>
  <div class="list-group-item">
    <label style="width:100px;">End value:</label>
    <input type="number" value="1" id="endval" />
  </div>
  <div class="list-group-item">
    <label style="width:100px;">Period:</label>
    <input type="number" value="1" id="yearval" />
  </div>
  <div class="list-group-item">
    <button class="btn btn-default pull-right" style="border:solid 1px; margin-right:3px;" onclick="calculate();">Go!</button>
  </div>
  <div class="list-group-item">
    <label style="width:100px;">Answer:</label>
    <input type="text" value="0%" id="growthval" readonly />
  </div>
</div>


<style>
  .input-group[type=number] {
    border:1px solid #aaa;
  }
</style>
<script type="text/javascript">
  function calculate(){
    var startval = parseInt($("#startval").val());
    var endval = parseInt($("#endval").val());
    var yearval = parseInt($("#yearval").val());

    var yearFrac = 1/yearval;
    var growthRate = (endval-startval)/startval;
    var growthval = (Math.pow(growthRate+1, yearFrac)-1)*100;
    var normalised = Math.round(growthval*100)/100;

    $("#growthval").val(normalised.toString() + "%" );
  }
</script>
