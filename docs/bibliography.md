---
layout: page
title: Bibliography
permalink: /bib/
nav_order: 1
---

Here, we provide a table of results for all the articles included in the systematic review. Similarly, we provide a table of studies that were excluded from analysis with exclusion reasons. We embeded a search function that allows multiple keyword search by placing a " " in between keywords, a custom search builder that allows multiple conditional search, and an export tool that allows copying and downloading data in csv format. Moreover, clicking the "green +" button allows you to view all the extracted and computed information of the article. For a key of exclusion reasons, see <a href="{{site.baseurl}}/key/">Key</a>.

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<script src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.12.1/js/dataTables.bootstrap.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/searchbuilder/1.3.4/js/dataTables.searchBuilder.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/searchbuilder/1.3.4/js/searchBuilder.bootstrap.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/datetime/1.1.2/js/dataTables.dateTime.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/responsive/2.3.0/js/dataTables.responsive.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/scroller/2.0.7/js/dataTables.scroller.min.js"></script>

<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/dataTables.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/datetime/1.1.2/css/dataTables.dateTime.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/searchbuilder/1.3.4/css/searchBuilder.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/responsive/2.3.0/css/responsive.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/scroller/2.0.7/css/scroller.dataTables.min.css">

<h2> Studies Included in Systematic Review </h2>
{% include include_table.html %}

<script type="text/javascript">
	$(".className").attr("style","");
	$(document).ready(function() {
	    var table = $('#itable').DataTable({
	    	dom: 'Bfrtip',
	    	pageLength: 25,
	        searchBuilder: true,
	        responsive: true,
	        columnDefs: [{ responsivePriority: 1, targets: 0 }],
			order: [[10, 'desc']],
			scrollY: 600,
	        scrollCollapse: false,
        	scroller: true
	    });
	    table.searchBuilder.container().prependTo(table.table().container());
	});
</script>

<br>

<h2> Studies not Included in Systematic Review </h2>
{% include exclude_table.html %}

<script type="text/javascript">
	$(".className").attr("style","");
	$(document).ready(function() {
	    var table = $('#etable').DataTable({
	    	dom: 'Bfrtip',
	    	pageLength: 25,
	        searchBuilder: true,
	        responsive: true,
			scrollY: 600,
	        scrollCollapse: false,
        	scroller: true
	    });
	    table.searchBuilder.container().prependTo(table.table().container());
	});
</script>
