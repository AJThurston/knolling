# Knolling
AJ Thurston

## Introduction

Originating from photography, knolling is the process of laying out
objects in a clean and tidy pattern. Knolling in data visualization is
an alternative to other bar charts where each response option occupies
its own axis, and each axis has a consistent width, to make for easier
and consistent comparisons across response options and groups.

## Comparison to other bar charts

Knolling offers some advantages over issues with other bar charts:

- Stacked bar charts are intuitive but can mask important response
  option differences as each response option can start as a different
  x-axis origin.

- Grouped bar charts force the data visualization maker to choose to
  compare either the group or the response options, but it is difficult
  to make comparisons across both.

- Diverging response option charts are less commonly used and can be
  complex to make. They also force the reader of the chart to interpret
  distance from the y-axis both left to right and right to left.

![](bar_chart_comparison.png)

## Templates

### PowerPoint

For most use cases, I would actually recommend using the [PowerPoint
template](https://github.com/AJThurston/knolling/raw/main/knolling.pptx).
Note, there is a `buffer` or scaling factor that is designed to maximize
the width of each response option column while leaving a bit of space
for a data label, so if the label’s position isn’t to your liking,
adjust the buffer to your liking. Note, the knolling chart in PowerPoint
is just a stacked bar chart with blank columns, so if you need to add
more response options you will need to add more blank columns for a
consistent look, and may need to adjust the axis lines as well.

### R using {gtExtra}

For repeated, HTML-based applications, I’ve replicated what is provided
inthe PowerPoint using {gt} and {gtExtras} for 2, 3, 4, and 5 response
options below.

``` r
library(gt)
library(gtExtras)
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ✔ ggplot2   3.5.0     ✔ tibble    3.2.1
    ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
    ✔ purrr     1.0.2     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(svglite)
library(ggplot2)
```

## Two Response Options

``` r
k2ro <-  tibble(
  Category = c("Category 1","Category 2", "Category 3", "Category 4"),
  Never = c(60,60,50,40),
  Always = c(40,40,50,60)
) 

k2ro %>%
  gt(rowname_col = "Category") %>%
  gt_plt_bar_pct(
    column = Never,
    width = 300,
    fill = "darkred",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = Always,
    width = 300,
    fill = "darkgreen",
    labels = TRUE,
    scaled = TRUE) %>%
  tab_options(table.width = pct(100))
```

<div>

<div id="hetawaphqm" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#hetawaphqm table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#hetawaphqm thead, #hetawaphqm tbody, #hetawaphqm tfoot, #hetawaphqm tr, #hetawaphqm td, #hetawaphqm th {
  border-style: none;
}
&#10;#hetawaphqm p {
  margin: 0;
  padding: 0;
}
&#10;#hetawaphqm .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: 100%;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#hetawaphqm .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#hetawaphqm .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#hetawaphqm .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#hetawaphqm .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#hetawaphqm .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#hetawaphqm .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#hetawaphqm .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#hetawaphqm .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#hetawaphqm .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#hetawaphqm .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#hetawaphqm .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#hetawaphqm .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#hetawaphqm .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#hetawaphqm .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#hetawaphqm .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#hetawaphqm .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#hetawaphqm .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#hetawaphqm .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#hetawaphqm .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#hetawaphqm .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#hetawaphqm .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#hetawaphqm .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#hetawaphqm .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#hetawaphqm .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#hetawaphqm .gt_left {
  text-align: left;
}
&#10;#hetawaphqm .gt_center {
  text-align: center;
}
&#10;#hetawaphqm .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#hetawaphqm .gt_font_normal {
  font-weight: normal;
}
&#10;#hetawaphqm .gt_font_bold {
  font-weight: bold;
}
&#10;#hetawaphqm .gt_font_italic {
  font-style: italic;
}
&#10;#hetawaphqm .gt_super {
  font-size: 65%;
}
&#10;#hetawaphqm .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#hetawaphqm .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#hetawaphqm .gt_indent_1 {
  text-indent: 5px;
}
&#10;#hetawaphqm .gt_indent_2 {
  text-indent: 10px;
}
&#10;#hetawaphqm .gt_indent_3 {
  text-indent: 15px;
}
&#10;#hetawaphqm .gt_indent_4 {
  text-indent: 20px;
}
&#10;#hetawaphqm .gt_indent_5 {
  text-indent: 25px;
}
</style>

<table class="gt_table" data-quarto-postprocess="true"
style="table-layout: fixed;; width: 100%"
data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<thead>
<tr class="header gt_col_headings">
<th class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col"></th>
<th id="Never" class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Never</th>
<th id="Always" class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Always</th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td id="stub_1_1" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 1</td>
<td class="gt_row gt_left" headers="stub_1_1 Never"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:60%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">60%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Always"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_2" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 2</td>
<td class="gt_row gt_left" headers="stub_1_2 Never"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:60%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">60%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Always"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
</tr>
<tr class="odd">
<td id="stub_1_3" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 3</td>
<td class="gt_row gt_left" headers="stub_1_3 Never"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:50%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">50%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Always"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:50%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">50%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_4" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 4</td>
<td class="gt_row gt_left" headers="stub_1_4 Never"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Always"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:60%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">60%</span>
</div>
</div></td>
</tr>
</tbody>
</table>

</div>

</div>

## Three Response Options

``` r
k3ro <- tibble(
  Category = c("Category 1", "Category 2", "Category 3", "Category 4"),
  Negative = c(20, 30, 40, 50),
  Neutral = c(30, 30, 30, 30),
  Positive = c(50, 40, 30, 20)
)

k3ro %>%
  gt(rowname_col = "Category") %>%
  gt_plt_bar_pct(
    column = Negative,
    width = 200,
    fill = "darkred",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = Neutral,
    width = 200,
    fill = "#565656",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = Positive,
    width = 200,
    fill = "darkgreen",
    labels = TRUE,
    scaled = TRUE) %>%
  tab_options(table.width = pct(100))
```

<div>

<div id="wqmqnfeyfq" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#wqmqnfeyfq table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#wqmqnfeyfq thead, #wqmqnfeyfq tbody, #wqmqnfeyfq tfoot, #wqmqnfeyfq tr, #wqmqnfeyfq td, #wqmqnfeyfq th {
  border-style: none;
}
&#10;#wqmqnfeyfq p {
  margin: 0;
  padding: 0;
}
&#10;#wqmqnfeyfq .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: 100%;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#wqmqnfeyfq .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#wqmqnfeyfq .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#wqmqnfeyfq .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#wqmqnfeyfq .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#wqmqnfeyfq .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#wqmqnfeyfq .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#wqmqnfeyfq .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#wqmqnfeyfq .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#wqmqnfeyfq .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#wqmqnfeyfq .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#wqmqnfeyfq .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#wqmqnfeyfq .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#wqmqnfeyfq .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#wqmqnfeyfq .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wqmqnfeyfq .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#wqmqnfeyfq .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#wqmqnfeyfq .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#wqmqnfeyfq .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wqmqnfeyfq .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#wqmqnfeyfq .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wqmqnfeyfq .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#wqmqnfeyfq .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wqmqnfeyfq .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#wqmqnfeyfq .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wqmqnfeyfq .gt_left {
  text-align: left;
}
&#10;#wqmqnfeyfq .gt_center {
  text-align: center;
}
&#10;#wqmqnfeyfq .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#wqmqnfeyfq .gt_font_normal {
  font-weight: normal;
}
&#10;#wqmqnfeyfq .gt_font_bold {
  font-weight: bold;
}
&#10;#wqmqnfeyfq .gt_font_italic {
  font-style: italic;
}
&#10;#wqmqnfeyfq .gt_super {
  font-size: 65%;
}
&#10;#wqmqnfeyfq .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#wqmqnfeyfq .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#wqmqnfeyfq .gt_indent_1 {
  text-indent: 5px;
}
&#10;#wqmqnfeyfq .gt_indent_2 {
  text-indent: 10px;
}
&#10;#wqmqnfeyfq .gt_indent_3 {
  text-indent: 15px;
}
&#10;#wqmqnfeyfq .gt_indent_4 {
  text-indent: 20px;
}
&#10;#wqmqnfeyfq .gt_indent_5 {
  text-indent: 25px;
}
</style>

<table class="gt_table" data-quarto-postprocess="true"
style="table-layout: fixed;; width: 100%"
data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<thead>
<tr class="header gt_col_headings">
<th class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col"></th>
<th id="Negative"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Negative</th>
<th id="Neutral" class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Neutral</th>
<th id="Positive"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Positive</th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td id="stub_1_1" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 1</td>
<td class="gt_row gt_left" headers="stub_1_1 Negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Neutral"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:50%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">50%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_2" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 2</td>
<td class="gt_row gt_left" headers="stub_1_2 Negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Neutral"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
</tr>
<tr class="odd">
<td id="stub_1_3" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 3</td>
<td class="gt_row gt_left" headers="stub_1_3 Negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Neutral"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_4" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 4</td>
<td class="gt_row gt_left" headers="stub_1_4 Negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:50%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">50%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Neutral"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
</tr>
</tbody>
</table>

</div>

</div>

## Four Response Options

``` r
k4ro <- tibble(
  Category = c("Category 1", "Category 2", "Category 3", "Category 4"),
  `Mostly negative` = c(10, 20, 30, 40),
  `Somewhat negative` = c(10, 20, 30, 20),
  `Somewhat positive` = c(30, 30, 20, 20),
  `Mostly positive` = c(50, 30, 20, 20)
) 

k4ro %>%
  gt(rowname_col = "Category") %>%
  gt_plt_bar_pct(
    column = `Mostly negative`,
    width = 150,
    fill = "darkred",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Somewhat negative`,
    width = 150,
    fill = "#CC3333",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Somewhat positive`,
    width = 150,
    fill = "#33CC33",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Mostly positive`,
    width = 150,
    fill = "darkgreen",
    labels = TRUE,
    scaled = TRUE) %>%
  tab_options(table.width = pct(100))
```

<div>

<div id="gumvkmfavs" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#gumvkmfavs table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#gumvkmfavs thead, #gumvkmfavs tbody, #gumvkmfavs tfoot, #gumvkmfavs tr, #gumvkmfavs td, #gumvkmfavs th {
  border-style: none;
}
&#10;#gumvkmfavs p {
  margin: 0;
  padding: 0;
}
&#10;#gumvkmfavs .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: 100%;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#gumvkmfavs .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#gumvkmfavs .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#gumvkmfavs .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#gumvkmfavs .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#gumvkmfavs .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#gumvkmfavs .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#gumvkmfavs .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#gumvkmfavs .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#gumvkmfavs .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#gumvkmfavs .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#gumvkmfavs .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#gumvkmfavs .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#gumvkmfavs .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#gumvkmfavs .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#gumvkmfavs .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#gumvkmfavs .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#gumvkmfavs .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#gumvkmfavs .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#gumvkmfavs .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#gumvkmfavs .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#gumvkmfavs .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#gumvkmfavs .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#gumvkmfavs .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#gumvkmfavs .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#gumvkmfavs .gt_left {
  text-align: left;
}
&#10;#gumvkmfavs .gt_center {
  text-align: center;
}
&#10;#gumvkmfavs .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#gumvkmfavs .gt_font_normal {
  font-weight: normal;
}
&#10;#gumvkmfavs .gt_font_bold {
  font-weight: bold;
}
&#10;#gumvkmfavs .gt_font_italic {
  font-style: italic;
}
&#10;#gumvkmfavs .gt_super {
  font-size: 65%;
}
&#10;#gumvkmfavs .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#gumvkmfavs .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#gumvkmfavs .gt_indent_1 {
  text-indent: 5px;
}
&#10;#gumvkmfavs .gt_indent_2 {
  text-indent: 10px;
}
&#10;#gumvkmfavs .gt_indent_3 {
  text-indent: 15px;
}
&#10;#gumvkmfavs .gt_indent_4 {
  text-indent: 20px;
}
&#10;#gumvkmfavs .gt_indent_5 {
  text-indent: 25px;
}
</style>

<table class="gt_table" data-quarto-postprocess="true"
style="table-layout: fixed;; width: 100%"
data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<thead>
<tr class="header gt_col_headings">
<th class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col"></th>
<th id="Mostly negative"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Mostly negative</th>
<th id="Somewhat negative"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Somewhat negative</th>
<th id="Somewhat positive"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Somewhat positive</th>
<th id="Mostly positive"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Mostly positive</th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td id="stub_1_1" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 1</td>
<td class="gt_row gt_left" headers="stub_1_1 Mostly negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:10%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:15px;font-weight:bold;font-size:10px;">10%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Somewhat negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:10%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:15px;font-weight:bold;font-size:10px;">10%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Somewhat positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Mostly positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:50%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">50%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_2" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 2</td>
<td class="gt_row gt_left" headers="stub_1_2 Mostly negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Somewhat negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Somewhat positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Mostly positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
</tr>
<tr class="odd">
<td id="stub_1_3" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 3</td>
<td class="gt_row gt_left" headers="stub_1_3 Mostly negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Somewhat negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Somewhat positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Mostly positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_4" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 4</td>
<td class="gt_row gt_left" headers="stub_1_4 Mostly negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Somewhat negative"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Somewhat positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Mostly positive"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
</tr>
</tbody>
</table>

</div>

</div>

## Five Response Options

``` r
k5ro <- tibble(
  Category = c("Category 1", "Category 2", "Category 3", "Category 4"),
  `Strongly disagree` = c(5, 10, 25, 40),
  `Somewhat disagree` = c(5, 10, 25, 20),
  `Neither agree nor disagree` = c(25, 20, 20, 20),
  `Somewhat agree` = c(20, 30, 20, 20),
  `Strongly agree` = c(45, 30, 10, 0)
)

k5ro %>%
  gt(rowname_col = "Category") %>%
  gt_plt_bar_pct(
    column = `Strongly disagree`,
    width = 120,
    fill = "darkred",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Somewhat disagree`,
    width = 120,
    fill = "#CC3333",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Neither agree nor disagree`,
    width = 120,
    fill = "#565656",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Somewhat agree`,
    width = 120,
    fill = "#33CC33",
    labels = TRUE,
    scaled = TRUE) %>%
  gt_plt_bar_pct(
    column = `Strongly agree`,
    width = 120,
    fill = "darkgreen",
    labels = TRUE,
    scaled = TRUE) %>%
  tab_options(table.width = pct(100))
```

<div>

<div id="wflidxakyx" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#wflidxakyx table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#wflidxakyx thead, #wflidxakyx tbody, #wflidxakyx tfoot, #wflidxakyx tr, #wflidxakyx td, #wflidxakyx th {
  border-style: none;
}
&#10;#wflidxakyx p {
  margin: 0;
  padding: 0;
}
&#10;#wflidxakyx .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: 100%;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#wflidxakyx .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#wflidxakyx .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#wflidxakyx .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#wflidxakyx .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#wflidxakyx .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#wflidxakyx .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#wflidxakyx .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#wflidxakyx .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#wflidxakyx .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#wflidxakyx .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#wflidxakyx .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#wflidxakyx .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#wflidxakyx .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#wflidxakyx .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wflidxakyx .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#wflidxakyx .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#wflidxakyx .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#wflidxakyx .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wflidxakyx .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#wflidxakyx .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wflidxakyx .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#wflidxakyx .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wflidxakyx .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#wflidxakyx .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#wflidxakyx .gt_left {
  text-align: left;
}
&#10;#wflidxakyx .gt_center {
  text-align: center;
}
&#10;#wflidxakyx .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#wflidxakyx .gt_font_normal {
  font-weight: normal;
}
&#10;#wflidxakyx .gt_font_bold {
  font-weight: bold;
}
&#10;#wflidxakyx .gt_font_italic {
  font-style: italic;
}
&#10;#wflidxakyx .gt_super {
  font-size: 65%;
}
&#10;#wflidxakyx .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#wflidxakyx .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#wflidxakyx .gt_indent_1 {
  text-indent: 5px;
}
&#10;#wflidxakyx .gt_indent_2 {
  text-indent: 10px;
}
&#10;#wflidxakyx .gt_indent_3 {
  text-indent: 15px;
}
&#10;#wflidxakyx .gt_indent_4 {
  text-indent: 20px;
}
&#10;#wflidxakyx .gt_indent_5 {
  text-indent: 25px;
}
</style>

<table class="gt_table" data-quarto-postprocess="true"
style="table-layout: fixed;; width: 100%"
data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<thead>
<tr class="header gt_col_headings">
<th class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col"></th>
<th id="Strongly disagree"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Strongly disagree</th>
<th id="Somewhat disagree"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Somewhat disagree</th>
<th id="Neither agree nor disagree"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Neither agree nor
disagree</th>
<th id="Somewhat agree"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Somewhat agree</th>
<th id="Strongly agree"
class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" scope="col">Strongly agree</th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td id="stub_1_1" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 1</td>
<td class="gt_row gt_left" headers="stub_1_1 Strongly disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:5%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:6px;font-weight:bold;font-size:10px;">5%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Somewhat disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:5%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:6px;font-weight:bold;font-size:10px;">5%</span>
</div>
</div></td>
<td class="gt_row gt_left"
headers="stub_1_1 Neither agree nor disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:25%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">25%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Somewhat agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_1 Strongly agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:45%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">45%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_2" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 2</td>
<td class="gt_row gt_left" headers="stub_1_2 Strongly disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:10%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:12px;font-weight:bold;font-size:10px;">10%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Somewhat disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:10%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">10%</span>
</div>
</div></td>
<td class="gt_row gt_left"
headers="stub_1_2 Neither agree nor disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Somewhat agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_2 Strongly agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:30%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">30%</span>
</div>
</div></td>
</tr>
<tr class="odd">
<td id="stub_1_3" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 3</td>
<td class="gt_row gt_left" headers="stub_1_3 Strongly disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:25%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">25%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Somewhat disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:25%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">25%</span>
</div>
</div></td>
<td class="gt_row gt_left"
headers="stub_1_3 Neither agree nor disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Somewhat agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_3 Strongly agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:10%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:12px;font-weight:bold;font-size:10px;">10%</span>
</div>
</div></td>
</tr>
<tr class="even">
<td id="stub_1_4" class="gt_row gt_left gt_stub"
data-quarto-table-cell-role="th" scope="row">Category 4</td>
<td class="gt_row gt_left" headers="stub_1_4 Strongly disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkred;width:40%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">40%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Somewhat disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#CC3333;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left"
headers="stub_1_4 Neither agree nor disagree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#565656;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#FFFFFF;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Somewhat agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:#33CC33;width:20%;height:16px;display:flex;align-items:center;justify-content:flex-start;position:relative;">
<span
style="color:#000000;position:absolute;left:0px;margin-left:5px;font-weight:bold;font-size:10px;">20%</span>
</div>
</div></td>
<td class="gt_row gt_left" headers="stub_1_4 Strongly agree"><div
style="flex-grow:1;margin-left:8px;background:#e1e1e1;">
<div
style="background:darkgreen;width:0%;height:16px;display:flex;align-items:center;justify-content:center;color:#000000;font-weight:bold;font-size:10px;position:relative;">
<span
style="color:#000000;position:absolute;left:0%;margin-left:0px;font-weight:bold;font-size:10px;">0%</span>
</div>
</div></td>
</tr>
</tbody>
</table>

</div>

</div>
