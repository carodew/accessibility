---
title: Tables
description: 'How we deal with tables'
permalink: /tables/
page_title: Tables
---

When tables are used to show data, the header cells that relate to the data cells need to be programatically linked. This makes table navigation for screen readers less painful. 

Simple tables can have 2 levels of headers. Each header cell should have `scope='col'` or `scope='row'`. 
Complex tables are tables with more than 2 levels of headers. Each header should be given a unique `id` and each data cell should have a `headers` attribute with each related header cells id listed. 

### Testing

1. Identify 'data' tables (layout tables are exempt)
2. View the table source code
3. Identify the table headers
  * Check for scope on simple tables
  * Check for id and headers on complex tables 

### Examples

#### Passes

##### Simple Table

<table>
	<tr>
		<th scope="col">
			Name
		</th>
		<th scope="col">
			Height
		</th>
		<th scope="col">
			Age
		</th>
	</tr>
	<tr>
		<td scope='row'>
			Walter
		</td>
		<td>6'4</td>
		<td>34</td>
	</tr>
	<tr>
		<td scope='row'>
			Steve
		</td>
		<td>5'4</td>
		<td>30</td>
	</tr>
</table>

```html
<table>
	<tr>
		<th scope="col">
			Name
		</th>
		<th scope="col">
			Height
		</th>
		<th scope="col">
			Age
		</th>
	</tr>
	<tr>
		<td scope='row'>
			Walter
		</td>
		<td>6'4</td>
		<td>34</td>
	</tr>
	<tr>
		<td scope='row'>
			Steve
		</td>
		<td>5'4</td>
		<td>30</td>
	</tr>
</table>
```

> Looking at this table, the column headers all relate to the cells below. This is done programatically with ```scope="col"```. Each height and age value is related to the person and this is done programatically with ```scope="row"```.

##### Complex table

<table>
	<tr>
		<th rowspan='2' id='name'>
			Name
		</th>
		<th colspan='2' id='height'>
			Height
		</th>
		<th rowspan='2' id='age'>
			Age
		</th>
	</tr>
	<tr>
		<th id='feet' headers='height'>
			Feet
		</th>
		<th id='inches' headers='height'>
			Inches
		</th>
	<tr>
		<td headers='name'>
			Walter
		</td>
		<td headers='height feet'>6</td>
		<td headers='height inches'>4</td>
		<td headers='age'>34</td>
	</tr>
	<tr>
		<td headers='name'>
			Steve
		</td>
		<td headers='height feet's>5</td>
		<td headers='height inches'>4</td>
		<td headers='age'>30</td>
	</tr>
</table>

```html
<table>
	<tr>
		<th rowspan='2' id='name'>
			Name
		</th>
		<th colspan='2' id='height'>
			Height
		</th>
		<th rowspan='2' id='age'>
			Age
		</th>
	</tr>
	<tr>
		<th id='feet' headers='height'>
			Feet
		</th>
		<th id='inches' headers='height'>
			Inches
		</th>
	<tr>
		<td headers='name' id='walter'>
			Walter
		</td>
		<td headers='height feet walter'>6</td>
		<td headers='height inches walter'>4</td>
		<td headers='age walter'>34</td>
	</tr>
	<tr>
		<td headers='name' id='steve'>
			Steve
		</td>
		<td headers='height feet steve's>5</td>
		<td headers='height inches steve'>4</td>
		<td headers='age steve'>30</td>
	</tr>
</table>
```

> This is an example of a complex table, all the cells are associated to their respective headers with the ```headers``` attribute. Most tables don't require this level of complexity. 
