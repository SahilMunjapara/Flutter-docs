---
layout: post
title: Scrolling in Flutter DataGrid | DataTable | Syncfusion
description: Learn here all about scrolling features of Syncfusion Flutter DataGrid (SfDataGrid) widget and more.
platform: flutter
control: SfDataGrid
documentation: ug
---

# Scrolling in Flutter DataGrid (SfDataGrid)

SfDataGrid provides support to scroll the content in both the horizontal and vertical direction. 

## Show Scrollbars always

You can show horizontal and vertical scrollbars always by using the [SfDataGrid.isScrollbarAlwaysShown](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/isScrollbarAlwaysShown.html) property. When the `isScrollbarAlwaysShown` is set to false, the scrollbar will be shown during scrolling and will fade out otherwise. When it is true, the scrollbar will always be visible and never fade out even after the scrolling.

N> The default value of `isScrollbarAlwaysShown` is false.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        isScrollbarAlwaysShown: true,
        columns: [
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
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Setting scroll physics for scroll bars

SfDataGrid allows you to set the [ScrollPhysics](https://api.flutter.dev/flutter/widgets/ScrollPhysics-class.html) for horizontal and vertical scrollbars to control how the scroll view should respond to user input by using [horizontalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/horizontalScrollPhysics.html) and [verticalScrollPhysics](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/verticalScrollPhysics.html) properties respectively.

N> The default values of `horizontalScrollPhysics` and `verticalScrollPhysics` properties are `AlwaysScrollableScrollPhysics()`.

The following example shows how to disable the horizontal and vertical scrolling by setting `NeverScrollableScrollPhysics()`.

{% tabs %}
{% highlight Dart %}

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: SfDataGrid(
        source: _employeeDataSource,
        horizontalScrollPhysics: NeverScrollableScrollPhysics(),
        verticalScrollPhysics: NeverScrollableScrollPhysics(),
        columns: [
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
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

## Programmatic scrolling

The Flutter DataTable provides support to scroll to a particular row and column index programmatically.

### Scroll to cell

Scroll programmatically to a particular cell can be achieved by passing the row and column index in the `scrollToCell` method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToCell` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToCell'),
          onPressed: () {
            _controller.scrollToCell(15, 2);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![Flutter DataTable shows programmatic scrolling to cell](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-cell.gif)

### Scroll to row

You can scroll programmatically to a particular row by passing the row index in the `scrollToRow` method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToRow` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToRow'),
          onPressed: () {
            _controller.scrollToRow(15);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to column

You can scroll programmatically to a particular column by passing the column index in the `scrollToColumn` method. SfDataGrid allows to enable or disable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToColumn` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToColumn'),
          onPressed: () {
            _controller.scrollToColumn(2);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

![Flutter DataTable shows programmatic scrolling to column](images/scrolling/flutter-datagrid-programmatic-scrolling-scroll-to-column.gif)

### Scroll to specific position

`SfDataGrid` allows to position the scrolled row or column in view programmatically by passing `DataGridScrollPosition` to `rowPosition` and `columnPosition` arguments respectively in `scrollToCell` and `position` argument of `scrollToRow` and `scrollToColumn` methods. Below are the four types of positions available,

`makeVisible`: Scroll to make a specified row/column visible in datagrid. If the specified row/column is already in view, scrolling will not occur.
`start`: Scroll to make the row/column positioned at the start of the datagrid.
`center`: Scroll to make the row/column positioned at the center of the datagrid.
`end`: Scroll to make the row/column positioned at the end of the datagrid.

N> The default value of `DataGridScrollPosition` is `Start`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToCell'),
          onPressed: () {
            _controller.scrollToCell(15, 2,
                canAnimate: true,
                rowPosition: DataGridScrollPosition.start,
                columnPosition: DataGridScrollPosition.start);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to vertical offset

The Flutter DataTable supports to scroll programmatically to a particular vertical offset by passing the offset value to the `scrollToVerticalOffset` method. Also, it allows to enable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToVerticalOffset` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToVerticalOffset'),
          onPressed: () {
            _controller.scrollToVerticalOffset(500);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

### Scroll to horizontal offset

The Flutter DataTable supports to scroll programmatically to a particular horizontal offset by passing the offset value to the `scrollToHorizontalOffset` method. Also, it allows to enable the scrolling animation by passing `true` to the `canAnimate` parameter in `scrollToHorizontalOffset` method. 

N> The default value of `canAnimate` is `false`.

{% tabs %}
{% highlight Dart %}

final DataGridController _controller = DataGridController();

 @override
 Widget build(BuildContext context) {
    return Scaffold(
      body: Column(children: [
        FlatButton(
          child: Text('ScrollToHorizontalOffset'),
          onPressed: () {
            _controller.scrollToHorizontalOffset(400);
          },
        ),
        Expanded( child:SfDataGrid(
          source: _employeeDataSource,
          columns: [
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
          controller: _controller,
        )),
    );
  }

{% endhighlight %}
{% endtabs %}

N> The vertical and horizontal scrolled offset can be retrieved by using `DataGridController.verticalOffset` and `DataGridController.horizontalOffset` properties.

## Listen the scroll changes

Listen to the vertical and horizontal scroll changes by using the [verticalScrollController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/verticalScrollController.html) and the [horizontalScrollController](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/horizontalScrollController.html) properties respectively . Set the listener in the `verticalScrollController` and the `horizontalScrollController` using the `addListener` method. By subscribing to this listener, the subscribed method in the sample level will be called on vertical or horizontal scrolling.

The following example demonstrates how to load more rows when vertical scrolling reaches 70% of the vertical maxScrollExtent,

{% tabs %}
{% highlight Dart %}

late _EmployeeDataSource employeeDataSource;
late ScrollController verticalScrollController;

  void verticalListner() {
    if (verticalScrollController.position.pixels >=
        verticalScrollController.position.maxScrollExtent * (70 / 100)) {
      employeeDataSource.loadMoreRows();
    }
  }

  @override
  void initState() {
    super.initState();
    employeeDataSource = _EmployeeDataSource();
    verticalScrollController = ScrollController()..addListener(verticalListner);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Flutter DataGrid Sample'),
      ),
      body: SfDataGrid(
          source: employeeDataSource,
          verticalScrollController: verticalScrollController,
          columnWidthMode: ColumnWidthMode.fill,
          columns: _getColumns()),
    );
  }

class _EmployeeDataSource extends DataGridSource {
  _EmployeeDataSource() {
    loadEmployees(25);
  }

  List<_Employee> employees = [];

  List<DataGridRow> dataGridRows = [];

  @override
  List<DataGridRow> get rows => dataGridRows;

  @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(cells: [
      Container(
        padding: EdgeInsets.all(8),
        alignment: Alignment.centerRight,
        child: Text(
          row.getCells()[0].value.toString(),
          overflow: TextOverflow.ellipsis,
        ),
      ),
      Container(
        padding: EdgeInsets.all(8),
        alignment: Alignment.centerRight,
        child: Text(
          row.getCells()[1].value.toString(),
          overflow: TextOverflow.ellipsis,
        ),
      ),
      Container(
        padding: EdgeInsets.all(8),
        alignment: Alignment.centerLeft,
        child: Text(
          row.getCells()[2].value.toString(),
          overflow: TextOverflow.ellipsis,
        ),
      ),
      Container(
        padding: EdgeInsets.all(8),
        alignment: Alignment.centerRight,
        child: Text(
          NumberFormat.currency(locale: 'en_US', symbol: '\$')
              .format(row.getCells()[3].value)
              .toString(),
          overflow: TextOverflow.ellipsis,
        ),
      ),
    ]);
  }

  void loadEmployees(int count) {
    final Random random = Random();
    final int startIndex = employees.isNotEmpty ? employees.length : 0,
        endIndex = startIndex + count;

    for (int i = startIndex; i < endIndex; i++) {
      var employee = _Employee(
        1000 + i,
        1700 + i,
        names[i < names.length ? i : random.nextInt(names.length - 1)],
        random.nextInt(1000) + random.nextDouble(),
        cities[random.nextInt(cities.length - 1)],
        1500.0 + random.nextInt(100),
      );
      employees.add(employee);
      dataGridRows.add(employee.getDataGridRow);
    }
  }

  void loadMoreRows() {
    loadEmployees(15);
    notifyListeners();
  }
}

{% endhighlight %}
{% endtabs %}

**NOTE**  
  Download demo application from [GitHub](https://github.com/SyncfusionExamples/how-to-load-data-lazily-when-scrolling-reaches-70-in-flutter-datatable-sfdatagrid).