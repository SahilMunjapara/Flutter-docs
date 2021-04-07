---
layout: post
title: Customize labels in a linear gauge | Linear Gauge widget| Syncfusion
description: Tutorial about the available styles of labels on Linear Gauge Flutter widget.| Flutter Linear Gauge widget|
platform: flutter
control: SfLinearGauge
documentation: ug
---

# Default Linear Gauge labels

The default style of axis labels are as below.

![Initialize linear gauge for axis](images/getting-started/default_linear_gauge.png)

## Customize Linear Gauge label styles

Axis labels can be customized using the [`axisLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/axisLabelStyle.html) property of [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html). The [`axisLabelStyle`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/axisLabelStyle.html) property have the below properties to customize the axis labels.

* `color` – Allows to customize the color of the labels.
* `fontFamily` – Allows to specify the font family for labels.
* `fontStyle` – Allows to specify the font style for labels.
* `fontWeight` – Allows to specify the font weight for labels.
* `fontSize` – Allows to specify the font size for labels.

{% highlight dart %} 

 @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: Scaffold(
            body: Center(
                child: SfLinearGauge(
                    axisLabelStyle: TextStyle(
                        color: Colors.red,
                        fontSize: 15,
                        fontStyle: FontStyle.italic,
                        fontWeight: FontWeight.bold,
                        fontFamily: 'Times')
                )
            )
        )
    );
  }

{% endhighlight %}

![Customize linear gauge axis label style](images/axis-labels/customize_label_style.png)

## Change label visibility

The [`showLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/showLabels.html) property of [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html) allows to show or hide the visibility of axis labels. The default value of the property is true.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(showLabels: false)) 
        )
    );
}

{% endhighlight %}

![Switch linear gauge axis label visibility](images/axis-labels/axis_label_visibility.png)

## Customize the interval between labels

The [`interval`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/interval.html) between labels can be customized using the interval property of [`SfLinearGauge`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge-class.html). The major ticks are generated based on this interval property.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(
                   interval: 20 
                )
            )
        )
    );
}

{% endhighlight %}

![Set label interval in axis track](images/axis-labels/axis_label_interval.png)

## Change the label position

The linear axis allows to position the labels either `inside` or `outside` the axis track using the [`labelsPosition`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/labelPosition.html) property. By default, labels are positioned `inside` the axis track.

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                child: SfLinearGauge(
                    tickPosition: LinearElementPosition.outside,
                    labelPosition: LinearLabelPosition.outside
                ), 
            )
        )
    );
}

{% endhighlight %}

![Set linear gauge label position](images/axis-labels/label-placement.png)


## Change the label offset

The [`labelOffset`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/labelOffset.html) property allows to adjust the distance between the tick-end and the labels. 

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                child: SfLinearGauge(
                  labelOffset:20
                ),             
            )
        )
    );
}

{% endhighlight %}

![Set linear gauge label offset](images/axis-labels/label_offset.png)

##  Customize the maximum number of visible labels

By default, a maximum of three labels are displayed for each 100 logical pixels in an axis. The maximum number of labels that should present within 100 logical pixels length can be customized using the [`maximumLabels`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/maximumLabels.html) property of the axis. 

{% highlight dart %} 

@override
Widget build(BuildContext context) {
  return MaterialApp(
      home: Scaffold(
          body: Center( 
                  child: SfLinearGauge(
                    maximumLabels: 5
                ) 
            )
        )
    );
}

{% endhighlight %}

![Set maximum number of labels in axis track](images/axis-labels/axis_label_visibility.png)

## Customize label text

You can format or change the whole numeric label text using the [`labelFormatterCallback`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/labelFormatterCallback.html).

{% highlight dart %}

SfLinearGauge(
    labelFormatterCallback: (label) {
      if (label == '0') {
        return 'Start';
      }

      if (label == '50') {
        return 'Mid';
      }

      if (label == '100') {
        return 'End';
      }

      return label;
    }
)

{% endhighlight %}

![Customize Label Text in axis track](images/axis-labels/custom_label_text.png)

## Number format

The [`numberFormat`](https://pub.dev/documentation/syncfusion_flutter_gauges/latest/gauges/SfLinearGauge/numberFormat.html) property is used to format the numeric labels. The default value of numberFormat property is null.


{% highlight dart %}

SfLinearGauge(
  numberFormat: NumberFormat("\$")
),

{% endhighlight %}

![Customize Label Format in Axis Label](images/axis-labels/axis_label_number_format.png)