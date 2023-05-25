# Flutter Pagewise

A library for widgets that load their content one page (or batch) at a time (also known as lazy-loading and pagination).

## Features

1. Load data one page at a time

2. Retry failed pages

3. Override the default loading, retry, and error widgets if desired

4. Manage loading of data more closely using a PagewiseLoadController

5. ListView and GridView implementations

6. SliverList and SliverGrid implementations

7. Extendability using inheritance

## Breaking Change Starting V1.0.0:

The library has been rewritten in version 1.0.0 to provide a more efficient implementation that does not require a totalCount parameter and shows only one loading sign when users scroll down. In addition, a new parameter has been added to itemBuilder callback to provide the index if needed by the user.

## Installing the library:

Like any other package, add the library to your pubspec.yaml dependencies:

   ```
   dependencies:
    flutter_pagewise:
   ```

Then import it wherever you want to use it:

   ```
   import 'package:flutter_pagewise/flutter_pagewise.dart';
   ```

## Using the library

The library provides the following widgets:

1. PagewiseGridView: A pagewise implementation of GridView. It could be used as follows:

   ```
   PagewiseGridView.count(
   pageSize: 10,
   crossAxisCount: 2,
   mainAxisSpacing: 8.0,
   crossAxisSpacing: 8.0,
   childAspectRatio: 0.555,
   padding: EdgeInsets.all(15.0),
   itemBuilder: (context, entry, index) {
   // return a widget that displays the entry's data
   },
   pageFuture: (pageIndex) {
   // return a Future that resolves to a list containing the page's data
   },
   );
   ```
   
2. PagewiseListView: A pagewise implementation of ListView. It could be used as follows:

   ```
   PagewiseListView(
   pageSize: 10,
   padding: EdgeInsets.all(15.0),
   itemBuilder: (context, entry, index) {
   // return a widget that displays the entry's data
   },
   pageFuture: (pageIndex) {
   // return a Future that resolves to a list containing the page's data
   }
   );
   ```
   
3. PagewiseSliverGrid: A pagewise implementation of SliverGrid. It could be used similar to PagewiseGridView for cases where a sliver is needed.

4. PagewiseSliverList: A pagewise implementation of SliverList. It could be used similar to PagewiseListView for cases where a sliver is needed.

The classes provide all the properties of ListViews and GridViews. In addition, you must provide the itemBuilder, which tells Pagewise how you want to render each element, and pageFuture, which Pagewise calls to fetch new pages. Please note that pageFuture must not return more values than mentioned in the pageSize parameter.


