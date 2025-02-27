---
layout: post
title: Getting started with Flutter Event Calendar widget | Syncfusion
description: Learn here about getting started with Syncfusion Event Calendar (SfCalendar) widget, its elements, and more.
platform: flutter
control: SfCalendar
documentation: ug
---

# Getting started with Flutter Event Calendar (SfCalendar)
This section explains the steps required to add the calendar widget and populate appointments to the calendar widget. This section covers only basic features needed to get started with Syncfusion calendar widget.

To get start quickly with our [Flutter event calendar widget](https://www.syncfusion.com/flutter-widgets/flutter-calendar), you can check on this video.

<style>#flutterEventCalendarVideoTutorial{width : 90% !important; height: 300px !important }</style>
<iframe id='flutterEventCalendarVideoTutorial' src='https://www.youtube.com/embed/3OROjbAQS8Y'></iframe>

N> You can also explore our [Flutter Calendar example](https://flutter.syncfusion.com/#/event-calendar/getting-started) to know how to render and configure the Flutter Examples.

## Add Flutter calendar to an application
Create a simple project using the instructions given in the [Getting Started with your first Flutter app](https://flutter.dev/docs/get-started/test-drive?tab=vscode#create-app) documentation.

**Add dependency**

Add the Syncfusion Flutter calendar dependency to your pubspec.yaml file.

{% highlight dart %}

dependencies:

syncfusion_flutter_calendar: ^xx.x.xx

{% endhighlight %}

N> Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter Calendar`](https://pub.dev/packages/syncfusion_flutter_calendar/versions) package.

**Get packages** 

Run the following command to get the required packages.

{% highlight dart %}

$ flutter pub get

{% endhighlight %}

**Import package**

Import the following package in your Dart code.

{% tabs %}
{% highlight Dart %}

import 'package:syncfusion_flutter_calendar/calendar.dart';

{% endhighlight %}
{% endtabs %}

## Initialize calendar

After importing the package, initialize the calendar widget as a child of any widget. Here, the calendar widget is added as a child of the scaffold widget.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
    child: SfCalendar(),
  ));
}
	
{% endhighlight %}
{% endtabs %}

![Calendar view](images/getting-started/dayview.png)

## Change different calendar views

The SfCalendar widget provides seven different types of views to display dates. It can be assigned to the widget constructor by using the [view](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/view.html) property. By default, the widget is assigned day view. The current date will be displayed initially for all the calendar views.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfCalendar(
    view: CalendarView.month,
  ));
}

{% endhighlight %}
{% endtabs %}

![Calendar view](images/getting-started/monthview.png)

## Add data source

The calendar widget has a built-in capability to handle appointment arrangement internally based on the appointment collections. You need to assign the created collection to the [dataSource](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/dataSource.html) property.
You can also map custom appointment data to our calendar.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SfCalendar(
    view: CalendarView.month,
    dataSource: MeetingDataSource(_getDataSource()),
    monthViewSettings: MonthViewSettings(
        appointmentDisplayMode: MonthAppointmentDisplayMode.appointment),
  ));
}

List<Meeting> _getDataSource() {
  final List<Meeting> meetings = <Meeting>[];
  final DateTime today = DateTime.now();
  final DateTime startTime =
      DateTime(today.year, today.month, today.day, 9, 0, 0);
  final DateTime endTime = startTime.add(const Duration(hours: 2));
  meetings.add(Meeting(
      'Conference', startTime, endTime, const Color(0xFF0F8644), false));
  return meetings;
}


class MeetingDataSource extends CalendarDataSource {
  MeetingDataSource(List<Meeting> source) {
    appointments = source;
  }

  @override
  DateTime getStartTime(int index) {
    return appointments![index].from;
  }

  @override
  DateTime getEndTime(int index) {
    return appointments![index].to;
  }

  @override
  String getSubject(int index) {
    return appointments![index].eventName;
  }

  @override
  Color getColor(int index) {
    return appointments![index].background;
  }

  @override
  bool isAllDay(int index) {
    return appointments![index].isAllDay;
  }
}

class Meeting {
  Meeting(this.eventName, this.from, this.to, this.background, this.isAllDay);

  String eventName;
  DateTime from;
  DateTime to;
  Color background;
  bool isAllDay;
}

{% endhighlight %}
{% endtabs %}

![AddData source](images/getting-started/datasource.png)

## Change first day of week

The calendar widget will be rendered with Sunday as the first day of the week, but you can customize it to any day by using the [firstDayOfWeek](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/firstDayOfWeek.html) property.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: SfCalendar(
    view: CalendarView.week,
    firstDayOfWeek: 1, // Monday
  ));
}

{% endhighlight %}
{% endtabs %}

![Change first day of week](images/getting-started/firstday-week.png)

## Initial selected date

You can programmatically select the specific calendar month cell, and time slot by setting corresponding date and time value to the [initialSelectedDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/initialSelectedDate.html) property of calendar. By default, it is null.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          initialSelectedDate: DateTime(2019, 12, 20, 12),
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial selected date](images/getting-started/initial-selected-date.png)

## Initial display date

You can change the initial display date of calendar by using the [initialDisplayDate](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/initialDisplayDate.html) property of calendar, which displays the calendar based on the given date time. By default, current date will be set as `initialDisplayDate`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          initialDisplayDate: DateTime(2019, 12, 20, 7, 30),
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Initial display date](images/getting-started/initial-display-date.png)

## Selection decoration

You can decorate the selection view of calendar by using the [selectionDecoration](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/selectionDecoration.html) property of Calendar.

{% tabs %}
{% highlight Dart %}

	@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          selectionDecoration: BoxDecoration(
            color: Colors.transparent,
            border: Border.all(color: Colors.red, width: 2),
            borderRadius: const BorderRadius.all(Radius.circular(4)),
            shape: BoxShape.rectangle,
          ),
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Selection decoration](images/getting-started/selection-decoration.png)

## Today highlight color

You can customize the today highlight color of calendar by using the [todayHighlightColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/todayHighlightColor.html) property in calendar, which will highlight the today text in calendar view header, month cell, and agenda view.

{% tabs %}
{% highlight Dart %}

	@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          todayHighlightColor: Colors.red,
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Today highlight color](images/getting-started/today-highlight-color.png)

## Cell border color

You can customize the vertical and horizontal line color of calendar by using the [cellBorderColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/cellBorderColor.html) property in calendar.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          cellBorderColor: Colors.blue,
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Cell border color](images/getting-started/cell-border-color.png)

## Background color

The calendar widgets background color can be customized by using the [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/backgroundColor.html) property in calendar.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
      body: Container(
        child: SfCalendar(
          view: CalendarView.week,
          backgroundColor: Colors.lightBlue,
        ),
      ),
    ),
  );
}

{% endhighlight %}
{% endtabs %}

![Background color](images/getting-started/calendar-background-color.png)

## Navigation arrow
Using the [showNavigationArrow](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/showNavigationArrow.html) property of the `SfCalendar`, you can navigate to the next or previous views of the calendar without swiping.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.month,
        showNavigationArrow: true,
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Show Navigation Arrow](images/getting-started/show-navigation-arrow.jpg)


>**NOTE** 
* The `showNavigationArrow` property is not applicable when the `view` is set to `CalendarView.schedule`.

## Cell end padding
You can customize the padding of appointment view end to make touch position for timeslot and month cell by using the [cellEndPadding](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/cellEndPadding.html) property in the calendar, which allows you to tap the calendar cell when the cell has appointments.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return MaterialApp(
    home: Scaffold(
        body: SfCalendar(
      view: CalendarView.month,
      cellEndPadding: 5,
      dataSource: _getCalendarDataSource(),
	  monthViewSettings: MonthViewSettings(
            appointmentDisplayMode:
                MonthAppointmentDisplayMode.appointment),
    )),
  );
}

{% endhighlight %}
{% endtabs %}

![Cell end padding](images/getting-started/cell-end-padding.png)

## Current time indicator

You can display the current time indicator in all timeslot views of SfCalendar by using the [showCurrentTimeIndicator](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/showCurrentTimeIndicator.html) property and you can also customize the color of current time indicator by using the [todayHighlightColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/todayHighlightColor.html) property. 

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
    return Container(
      child: SfCalendar(
        view: CalendarView.day,
        showCurrentTimeIndicator: true,
              ),
  );
  }

{% endhighlight %}
{% endtabs %}

![showCurrentTimeIndicator](images/getting-started/current-time-indicator.png)

## Week number

Display the Week number of the year in month, week and work week views of the `SfCalendar` by setting the [showWeekNumber](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/SfCalendar/showWeekNumber.html) property as true and by default it is false. Week numbers will be displayed based on the ISO standard.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
          view: CalendarView.month,
          showWeekNumber: true,
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Week Number in Flutter Calendar](images\getting-started\flutter-calendar-week-number.png)

## Week number appearance

Customize the Week number text style of the calendar by using the [WeekNumberStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekNumberStyle-class.html) property. Allows to customize the [textStyle](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekNumberStyle/textStyle.html) and the [backgroundColor](https://pub.dev/documentation/syncfusion_flutter_calendar/latest/calendar/WeekNumberStyle/backgroundColor.html) in the Week number of the calendar.

{% tabs %}
{% highlight Dart %}

@override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: SfCalendar(
          view: CalendarView.month,
          showWeekNumber: true,
          weekNumberStyle: const WeekNumberStyle(
            backgroundColor: Colors.pink,
            textStyle: TextStyle(color: Colors.white, fontSize: 15),
          ),
        ),
      ),
    );
  }

{% endhighlight %}
{% endtabs %}

![Week Number Appearance in Flutter Calendar](images\getting-started\flutter-calendar-week-number-appearance.png)

Get the complete "getting started" sample from [here](https://github.com/SyncfusionExamples/flutter-calendar).

## See also

* [How to switch between views of the event calendar in Flutter?](https://www.syncfusion.com/kb/10944/how-to-switch-between-views-of-the-event-calendar-in-flutter)
* [How to update event calendar (SfCalendar) DisplayDate using showDatePicker in flutter](https://www.syncfusion.com/kb/11010/how-to-update-event-calendar-sfcalendar-displaydate-using-showdatepicker-in-flutter)
* [How can we move to specific time while switching from month to day view in Flutter event calendar](https://www.syncfusion.com/kb/10943/how-can-we-move-to-specific-time-while-switching-from-month-to-day-view-in-flutter-event)
* [How to customize the cell border in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12118/how-to-customize-the-cell-border-in-the-flutter-event-calendar-sfcalendar)
* [How to apply theming in Flutter event calendar (SfCalendar)?](https://www.syncfusion.com/kb/11899/how-to-apply-theming-in-flutter-event-calendar-sfcalendar)
* [How to add an image as background in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12243/how-to-add-an-image-as-background-in-the-flutter-event-calendar-sfcalendar)
* [How to change the first day of week in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12222/how-to-change-the-first-day-of-week-in-the-flutter-event-calendar-sfcalendar)
* [How to interact with event calendar cell when appointments loaded in the Flutter (SfCalendar)](https://www.syncfusion.com/kb/12218/how-to-interact-with-event-calendar-cell-when-appointments-loaded-in-the-flutter-sfcalendar)
* [How to customize the selection using decoration in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12245/how-to-customize-the-selection-using-decoration-in-the-flutter-event-calendar-sfcalendar)
* [How to navigate to the previous or next views using navigation arrows in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12247/how-to-navigate-to-the-previous-or-next-views-using-navigation-arrows-in-the-flutter-event)
* [How to customize the current day color in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12336/how-to-customize-the-current-day-color-in-the-flutter-event-calendar-sfcalendar)
* [How to show a particular week in a day view of Flutter event calendar(SfCalendar)](https://www.syncfusion.com/kb/12310/how-to-show-a-particular-week-in-a-day-view-of-flutter-event-calendarsfcalendar)
* [How to customize the selection using decoration in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12245/how-to-customize-the-selection-using-decoration-in-the-flutter-event-calendar-sfcalendar)
* [How to format the view header day and date in the Flutter event calendar (SfCalendar)](https://www.syncfusion.com/kb/12339/how-to-format-the-view-header-day-and-date-in-the-flutter-event-calendar-sfcalendar)