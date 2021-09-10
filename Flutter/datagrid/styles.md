---
layout: post
title: Styling feature in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about how to customize the appearance of DataGrid in Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Styling in Flutter DataGrid (SfDataGrid)

The DataGrid supports to change the appearance of the grid by using the [SfDataGridThemeData](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData-class.html) in [SfDataGridTheme](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridTheme-class.html). The DataGrid should be wrapped inside the `SfDataGridTheme`.


## Change the header background color

Change the header background color by using [SfDataGridThemeData.headerColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerColor.html) property.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGridTheme(
          data: SfDataGridThemeData(headerColor: const Color(0xff009889)),
          child: SfDataGrid(
              source: _employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.all(16.0),
                        alignment: Alignment.center,
                        child: Text(
                          'ID',
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text('Name'))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text('Salary'))),
              ])));
}
{% endhighlight %}
{% endtabs %}

![flutter datagrid header background color](images/styles/flutter-datagrid-column-header-styling.png)

## Change the header hover color

Change the color of the header on hovering by using the [headerHoverColor]( https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/headerHoverColor.html) property.

N> This is applicable for web and desktop platforms.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: SfDataGridTheme(
          data: SfDataGridThemeData(headerHoverColor: Colors.yellow),
          child: SfDataGrid(
              source: _employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                    columnName: 'id',
                    label: Container(
                        padding: EdgeInsets.all(16.0),
                        alignment: Alignment.center,
                        child: Text(
                          'ID',
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text('Name'))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: Text('Salary'))),
              ])));
}
{% endhighlight %}
{% endtabs %}

![flutter datagrid header hovering](images/styles/flutter-datagrid-header-highlight.gif)

## Styling grid lines

Color and thickness of the grid lines can be changed by using the [SfDataGridThemeData.gridLineColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineColor.html) and [SfDataGridThemeData.gridLineStrokeWidth](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/gridLineStrokeWidth.html) properties.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGridTheme(
          data: SfDataGridThemeData(
              gridLineColor: Colors.amber, gridLineStrokeWidth: 3.0),
          child: SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                    padding: EdgeInsets.symmetric(horizontal: 16.0),
                    alignment: Alignment.centerRight,
                    child: Text(
                      'ID',
                      overflow: TextOverflow.ellipsis,
                    ))),
            GridColumn(
                columnName: 'name',
                label: Container(
                    padding: EdgeInsets.symmetric(horizontal: 16.0),
                    alignment: Alignment.centerLeft,
                    child: Text(
                      'Name',
                      overflow: TextOverflow.ellipsis,
                    ))),
            GridColumn(
                columnName: 'designation',
                label: Container(
                    padding: EdgeInsets.symmetric(horizontal: 16.0),
                    alignment: Alignment.centerLeft,
                    child: Text(
                      'Designation',
                      overflow: TextOverflow.ellipsis,
                    ))),
            GridColumn(
                columnName: 'salary',
                label: Container(
                    padding: EdgeInsets.symmetric(horizontal: 16.0),
                    alignment: Alignment.centerRight,
                    child: Text(
                      'Salary',
                      overflow: TextOverflow.ellipsis,
                    ))),
          ])));
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows customizing the grid lines](images/styles/flutter-datagrid-gridline-customization.png)

## Show vertical and horizontal grid lines

To show the vertical and horizontal gridlines, use the following properties. 

* [SfDataGrid.gridLinesVisibility](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/gridLinesVisibility.html): To set the border lines for the cells other than header and stacked header cells. 
* [SfDataGrid.headerGridLinesVisibility](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/headerGridLinesVisibility.html): To set the border lines only for header and stacked header cells.

The following are the list of options available to customize gridlines,

* Vertical
* Horizontal
* Both
* None

The following code describes how to show vertical and horizontal grid lines for the `SfDataGrid`.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfDataGrid(
        source: _employeeDataSource,
        columns: <GridColumn>[
          GridColumn(
              columnName: 'id',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'ID',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'name',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Name',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'designation',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text(
                    'Designation',
                    overflow: TextOverflow.ellipsis,
                  ))),
          GridColumn(
              columnName: 'salary',
              label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text(
                    'Salary',
                    overflow: TextOverflow.ellipsis,
                  ))),
        ],
        gridLinesVisibility: GridLinesVisibility.both,
        headerGridLinesVisibility: GridLinesVisibility.both),
  );
}
    
{% endhighlight %}
{% endtabs %}

![flutter datagrid shows both grid lines](images/styles/flutter-datagrid-gridlines.png)

## Disable the row highlighting

By default, the row highlighting on hovering support is enabled for the web and desktop platforms. Disable the row highlighting by setting the [SfDataGrid.highlightRowOnHover](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/highlightRowOnHover.html) property to `false`.

N> This is applicable for web and desktop platforms.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGrid(
          highlightRowOnHover: false,
          source: _employeeDataSource,
          columns: <GridColumn>[
        GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text('ID'),
            )),
        GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text('Name'),
            )),
        GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerLeft,
              child: Text('Designation'),
            )),
        GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.symmetric(horizontal: 16.0),
              alignment: Alignment.centerRight,
              child: Text('Salary'),
            )),
      ]));
}
    
{% endhighlight %}
{% endtabs %}

## Change the row highlighting background color and text style

Change the row highlighting color and text style by using the [SfDataGridThemeData.rowHoverColor](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/rowHoverColor.html) and the [SfDataGridThemeData.rowHoverTextStyle](https://pub.dev/documentation/syncfusion_flutter_core/latest/theme/SfDataGridThemeData/rowHoverTextStyle.html) properties.

{% tabs %}
{% highlight Dart %} 

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfDataGridTheme(
          data: SfDataGridThemeData(
              rowHoverColor: Colors.yellow,
              rowHoverTextStyle: TextStyle(
                color: Colors.red,
                fontSize: 14,
              )),
          child: SfDataGrid(source: _employeeDataSource, columns: <GridColumn>[
            GridColumn(
                columnName: 'id',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text('ID'),
                )),
            GridColumn(
                columnName: 'name',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text('Name'),
                )),
            GridColumn(
                columnName: 'designation',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerLeft,
                  child: Text('Designation'),
                )),
            GridColumn(
                columnName: 'salary',
                label: Container(
                  padding: EdgeInsets.symmetric(horizontal: 16.0),
                  alignment: Alignment.centerRight,
                  child: Text('Salary'),
                )),
          ])));
}
{% endhighlight %}
{% endtabs %}

![flutter datagrid highlight rows](images/styles/flutter-datagrid-highlight-rows.gif)

