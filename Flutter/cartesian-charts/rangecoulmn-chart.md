---
layout: post
title: Range column Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about Range column Chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Range column Chart in Flutter Cartesian Charts (SfCartesianChart)

To render a range column chart, create an instance of [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) and add to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). 

Since the [`RangeColumnSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/RangeColumnSeries-class.html) requires two Y values for a point, your data should contain high and low values. High and low value specifies the maximum and minimum range of the point. 

* [`highValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/highValueMapper.html) - field in the data source, which is considered as high value for the data points.
* [`lowValueMapper`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/lowValueMapper.html) - field in the data source, which is considered as low value for the data points. 

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}

![Range column chart](images/cartesian-chart-types/range_column.jpg)

## Data label

In the range column chart when data label is enabled, by default there will be two values displayed namely, high and low, but in the other types of charts, only y value will be displayed.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true, 
                                    labelAlignment: ChartDataLabelAlignment.top
                                ),
                            )
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Range column datalabel](images/cartesian-chart-types/range_column_datalabel.jpg)

## Transposed range column

The [`isTransposed`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/isTransposed.html) property of [`CartesianSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries-class.html) is used to transpose the horizontal and vertical axes, to view the data in a different perspective. Using this feature, you can render range column chart.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        isTransposed: true,
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            RangeColumnSeries<ChartData, String>(
                                dataSource: <ChartData>[
                                    ChartData('Jan', 3, 9),
                                    ChartData('Feb', 4, 11),
                                    ChartData('Mar', 6, 13),
                                    ChartData('Apr', 9, 17),
                                    ChartData('May', 12, 20),
                                ],
                                xValueMapper: (ChartData sales, _) => sales.x,
                                lowValueMapper: (ChartData sales, _) => sales.low,
                                highValueMapper: (ChartData sales, _) => sales.high,
                            )
                        ]
                    )
                )   
            )
        );
    }

    class ChartData {
        ChartData(this.x, this.high, this.low);
            final String x;
            final double high;
            final double low;
    }

{% endhighlight %}