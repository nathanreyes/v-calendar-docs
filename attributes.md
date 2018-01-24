# Attributes

Attributes are what bring `v-calendar` to life. They are simply visual decorators that can be applied to specific calendar dates.

<p align='center'>
  <img src='./gitbook/images/readme/welcome-1.png' title='Calendar with attributes' width='500'>
</p>

As mentioned in the introduction, there are many kinds of attributes you can configure, including the following:

  * Highlights
  * Dots
  * Bars
  * Content Styles (hovered and nonhovered)
  * Popovers

Any one or more of these attribute types may be combined into one single attribute object, and you can supply as many attributes as you want, like so:

```html
<v-calendar
  :attributes='attributes'>
</v-calendar>
```

```javascript
...
data() {
  return {
    // Attributes are supplied as an array
    attributes: [
      // This is a single attribute
      {
        // An optional key can be used for retrieving this attribute later,
        // and will most likely be derived from your data object
        key: 1,
        // The attribute can contain any of the following object types
        highlight: { ... },
        dot: { ... },
        bar: { ... },
        popover: { ... },
        contentStyle: { ... },
        contentHoverStyle: { ... },
        // Supply your custom data object for later access, if needed
        customData: { ... },
        // We also need some dates to know where to display the attribute
        // We use a single date here, but it could also be a date range
        //  or a complex date pattern.
        // Arrays are also allowed
        dates: new Date(),
        // You can optionally provide dates to exclude.
        // All other dates are used by the attributed.
        excludeDates: null,
        // Think of `order` like `z-index`
        order: 0
      }
    ];
  }
}
```

### Using `customData`

As well as specifying the attribute types we would like to display, note that you can also supply a `customData` property to link your custom data object. Just think of it as a way to tag the attribute with your data. The reason you might want to use this property becomes obvious as you begin to use the calendar. For example, if a user clicks on a calendar day that is displaying the attribute, you might want to react to that that click, so you will need to know that data associated with that attribute.

### Using `order`

By default, attributes are ordered to display the most information possible. For example, when attributes with highlighted regions overlap, single date regions appear above date range regions, and date ranges with a later start date appear above those with an earlier start date. 

<p align='center'>
  <img src='./gitbook/images/attributes/order.png' title='Ordering with highlights' width='200'>
</p>

If you would like to force an attribute to display above (or before) all others and override these rules, assign an order value greater than 0.

### Using `dates`

We also need to provide a date, date range (with or without patterns), or array of either. We'll cover more about how to use dates later in this section, but just remember that if you are having trouble with your attributes not showing up in the calendar, it might be because you forgot to supply the dates.
