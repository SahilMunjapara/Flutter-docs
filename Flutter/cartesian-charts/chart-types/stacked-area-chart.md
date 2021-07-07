---
layout: post
title: Stacked area Chart in Flutter Cartesian Charts widget | Syncfusion 
description: Learn here all about stacked area chart of Syncfusion Flutter Cartesian Charts (SfCartesianChart) widget and more.
platform: flutter
control: Chart
documentation: ug
---

# Stacked area Chart in Flutter Cartesian Charts (SfCartesianChart)

To create a Flutter stacked area chart quickly, you can check this video.

<style>#flutterstackedareaChartTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterstackedareaChartTutorial' src='https://www.youtube.com/embed/NCUDBD_ClHo'></iframe>

To render a stacked area chart, create an instance of [`StackedAreaSeries`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries-class.html), and add it to the [`series`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart/series.html) collection property of [`SfCartesianChart`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/SfCartesianChart-class.html). The following properties can be used to customize the appearance of stacked line series:

* [`color`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/color.html) - changes the color of the line.
* [`opacity`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/opacity.html) - controls the transparency of the chart series.
* [`borderWidth`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderWidth.html) - changes the stroke width of the series.
* [`borderColor`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/CartesianSeries/borderColor.html) - changes the stroke color of the series.


{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, String>(
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area](cartesian-chart-types-images/stacked_area.jpg)

## Grouping series

You can group and stack the similar stacked series types using the [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) property of stacked series. The stacked series that contains the same [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html) will be stacked in a single group.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area grouping](cartesian-chart-types-images/stacked_area_grouping.jpg)

## Display cumulative values

You can show the cumulative data label values using the [`showCumulativeValues`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/DataLabelSettings/showCumulativeValues.html) property. If the series are grouped using [`groupName`](https://pub.dev/documentation/syncfusion_flutter_charts/latest/charts/StackedAreaSeries/groupName.html), then cumulative values will be shown based on grouping.

{% highlight dart %} 
    
    @override
    Widget build(BuildContext context) {
         return Scaffold(
            body: Center(
                child: Container(
                    child: SfCartesianChart(
                        primaryXAxis: CategoryAxis(),
                        series: <ChartSeries>[
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y1
                            ),
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group B',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y2
                            ),
                            StackedAreaSeries<ChartData, String>(
                                groupName: 'Group A',
                                dataLabelSettings: DataLabelSettings(
                                    isVisible: true,
                                    showCumulativeValues: true,
                                    useSeriesColor: true
                                ),
                                dataSource: chartData,
                                xValueMapper: (ChartData sales, _) => sales.x,
                                yValueMapper: (ChartData sales, _) => sales.y3
                            ),
                        ]
                    )
                )   
            )
        );
    }

{% endhighlight %}

![Stacked area cumulative](cartesian-chart-types-images/stacked_area_cumulative.jpg)