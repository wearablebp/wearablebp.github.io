---
layout: page
title: Benchmarks
permalink: /benchmarks/
---

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

<link rel="stylesheet" type="text/css" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/dataTables.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/datetime/1.1.2/css/dataTables.dateTime.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/searchbuilder/1.3.4/css/searchBuilder.bootstrap.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/responsive/2.3.0/css/responsive.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.12.1/css/jquery.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/2.2.3/css/buttons.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/scroller/2.0.7/css/scroller.dataTables.min.css">

<font size="4"> Here, you can find a list of benchmarked algorithms, a searable table of available BP estimation code, and methodologies. To contribute to benchmarking, please follow the code submission guidelines and fill out this form. </font> <br>

{% include replicated_ed_scatter.html %}
<br>

<script type="text/javascript">
	$(".className").attr("style","");
	$(document).ready(function() {
	    var table = $('#btable').DataTable({
	    	dom: 'Bfrtip',
	    	pageLength: 25,
	        searchBuilder: true,
	        buttons: ['copy', 'csv'],
			order: [[2, 'desc']],
			scrollY: 600,
	        scrollCollapse: false,
        	// scroller: true,
        	deferRender:    true,
	    });
	    table.searchBuilder.container().prependTo(table.table().container());
	});
</script>


<font size="5"> Open Contribution Benchmarking </font> <br>

<font size="4">

It is important for a study to have reproducible results so the algorithms can be tested on other datasets for validity. Not only do these algorithms include estimation models, but they also include the data filtering algorithms that may shift the training and testing set distributions. We benchmark the data filtering algorithms and model combinations on publically available datasets. The implementation was done based on the code provided (on GitHub) and/or the details of the algorithms presented in the paper.

Moreover, reproducibility is not only limited to software. Some studies involve using unconventional sensors. Although developing new devices is important for exploratory research, these devices are not verifiable by an external party. In addition to transparent hardware, there needs to be more transparency in experimental protocols. For example, the contact pressure is known to affect waveform morphology. Since feature extraction techniques rely on waveform morphology to detect key points, devices used in one study may not yield the same results without standardization of experimental protocols. Some studies may use a PPG sensor with a different spring constant.

To tackle this, we referee a a table of benchmarks for wearable BP montoring and provide a machine learning pipeline for BP estimation. A diagram of the pipline is shown below in Fig. .

{% include benchmark_diagram.svg %}

Every benchmark that will be reported here will follow strict guidelines on sharing code and reporting results. We provide an update form for researchers to improve upon existing benchmarks and add new benchmarks. Finally, the benchmarks currently only cover ECG and PPG. However, as wearable sensors become cheaper and more ubiquitous, the benchmarks will be expanded to include them.

</font> <br>

<font size="5"> Available Third-party Code </font> <br>

<font size="4">  We provide a table of code and dataset availability for all the articles included in the systematic review. We embeded a search function that allows multiple keyword search by placing a " " in between keywords, a custom search builder that allows multiple conditional search, and an export tool that allows copying and downloading data in csv format. </font>
<br>
<font size="5"> Available Code Search Methodology </font>

<font size="4">
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
</font>



<br> 
<font size="5"> Available Code Search Table </font>

{% include availability_table.html %}

<script type="text/javascript">
	$(".className").attr("style","");
	$(document).ready(function() {
	    var table = $('#atable').DataTable({
	    	dom: 'Bfrtip',
	    	pageLength: 25,
	        searchBuilder: true,
	        buttons: ['copy', 'csv'],
			order: [[2, 'desc']],
			scrollY: 600,
	        scrollCollapse: false,
        	// scroller: true,
        	deferRender:    true,
	    });
	    table.searchBuilder.container().prependTo(table.table().container());
	});
</script>
