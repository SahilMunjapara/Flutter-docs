---
layout: post
title: Interaction modes of Syncfusion Flutter PDF Viewer | Syncfusion
description: This section explains about how to enable the different interaction modes in the Flutter PDF Viewer plugin.
platform: Flutter
control: SfPdfViewer
documentation: ug
---

# Interaction modes in Flutter PDF Viewer (SfPdfViewer)

The [SfPdfViewer](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer-class.html) supports following interaction modes for easy interaction with the PDF documents on a desktop web browser,

* selection
* pan

N> On a touch device, setting the `[interactionMode](https://pub.dev/documentation/syncfusion_flutter_pdfviewer/latest/pdfviewer/SfPdfViewer/interactionMode.html)` property to `selection` mode will have no effect since panning is the default mode for scrolling and the selection is made by long pressing a word in the document.

## Selection mode

By default, `selection` interaction mode will be enabled on a desktop web browser and allows users to select and copy text from the PDF files. This is helpful for copying and sharing text content. Refer to the following code to enable the `selection` mode in `SfPdfViewer`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf', 
              interactionMode: PdfInteractionMode.selection)));
}

{% endhighlight %}
{% endtabs %}

## Pan mode

In `pan` mode, the dragging and scrolling of the pages can be performed in any direction using mouse and touch interactions on a desktop web browser, but the text selection cannot be performed. Refer to the following code to enable the `pan` mode in `SfPdfViewer`.

{% tabs %}
{% highlight Dart %}

@override
Widget build(BuildContext context) {
  return Scaffold(
      body: Container(
          child: SfPdfViewer.network(
              'http://ebooks.syncfusion.com/downloads/flutter-succinctly/flutter-succinctly.pdf', 
              interactionMode: PdfInteractionMode.pan)));
}

{% endhighlight %}
{% endtabs %}