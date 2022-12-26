---
layout: page
title: Code
permalink: /code/
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<script src="https://code.jquery.com/jquery-3.5.1.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.12.1/js/jquery.dataTables.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/1.12.1/js/dataTables.bootstrap.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/searchbuilder/1.3.4/js/dataTables.searchBuilder.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/searchbuilder/1.3.4/js/searchBuilder.bootstrap.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/datetime/1.1.2/js/dataTables.dateTime.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/responsive/2.3.0/js/dataTables.responsive.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/dataTables.buttons.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/pdfmake.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.53/vfs_fonts.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.html5.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>
<script type="text/javascript" src="https://cdn.datatables.net/scroller/2.0.7/js/dataTables.scroller.min.js"></script>

<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/dataTables.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/datetime/1.1.2/css/dataTables.dateTime.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/searchbuilder/1.3.4/css/searchBuilder.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/responsive/2.3.0/css/responsive.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/2.2.3/css/buttons.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/scroller/2.0.7/css/scroller.dataTables.min.css">

Please see the Wearable BP on [GitHub](https://github.com/wearablebp/) for code to reproduce Systematic Review results and visuals.

<h2> Available Third-party Code </h2>

We provide a table of code and dataset availability for all the articles included in the systematic review. We embeded a search function that allows multiple keyword search by placing a " " in between keywords, a custom search builder that allows multiple conditional search, and an export tool that allows copying and downloading data in csv format.
<br>

<h2> Available Code Search Methodology </h2>

<ol>
	<li> Search "code", "availability", "available", "github" in article </li>
	<li> Search first three authors on github </li>
	<li> If no results, mark Original Model Implementation Availability as Unavailable </li>
	<li> If github profile found without code availabiltiy, mark Original Model Implementation Availability as "Unavailable. Check at [github profile url]"</li>
	<li> If code exists in public domain, mark Original Model Implementation Availability as "Available at [code repository url]" </li>
	<li> If code exists in public domain but without exact dataset or pre-processing code, mark as "Unavailable" </li>
	<li> If code or data is available upon request, mark as "Available upon request" </li>
	<li> If exact dataset and/or code to attain exact dataset used to train model exists in public domain, mark as "Available" </li>
	<li> If caveats exist, insert note after "Unavailable" or "Available". </li>
</ol>



<br> 
<font size="5"> Code Availability </font>

{% include availability_table.html %}

<script type="text/javascript">
	$(".className").attr("style","");
	$(document).ready(function() {
	    var table = $('#atable').DataTable({
	    	dom: 'Bfrtip',
	    	pageLength: 25,
	        searchBuilder: true,
	        responsive: true,
	        buttons: ['copy', 'csv'],
			scrollY: 600,
	        scrollCollapse: false,
        	scroller: true
	    });
	    table.searchBuilder.container().prependTo(table.table().container());
	});
</script>


<h2> Other Tools </h2>

| Package | Description
|[Waveform Database Software Package (WFDB) for MATLAB and Octave](https://physionet.org/content/wfdb-matlab/0.10.0/) | large collection of software for processing and analyzing physiological waveforms from PhysioNet
|[PPGraw](https://github.com/fwolling/PPGraw) | Code from [Wolling et al., 2020](https://dl.acm.org/doi/10.1145/3419016.3431485), that applies decision metrics to characterize unfiltered and raw signals
