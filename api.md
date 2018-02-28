# API

## Theme Styles

| Style | Target Area | Default |
| ----- | ----------- | ------- |
| `wrapper` | Wrapper for both single and double-paned calendars. | `{ backgroundColor: '#fafafa', border: '1px solid #dadada' }` |
| `verticalDivider` | Vertical divider that appears when calendar is double-paned. This style can be overriden by  `headerVerticalDivider`, `weekdayVerticalDivider`, or `weeksVerticalDivider` for those specific sections if necessary. | `{ borderLeft: '1px solid #dadada' }` |
| `header` | Header section that encapsulates arrows and title. | `null` |
| `headerTitle` | Header title. | `null` |
| `headerArrows` | Header arrows that can be styled just like a font. | `null` |
| `headerVerticalDivider` | Vertical divider that appears in the header section when calendar is double paned. This style overrides `verticalDivider` for the header section. | `null` |
| `headerHorizontalDivider` | Horizontal divider that appears just below header section. | `null` |
| `weekdays` | Weekday section that encapsulates all the weekday labels. | `null` |
| `weekdaysVerticalDivider` | Vertical divider that appears in the weekdays section when calendar is double paned. This style overrides `verticalDivider` for the weekdays section. | `null` |
| `weekdaysHorizontalDivider` | Horizontal divider that appears just below weekdays section. | `null` |
| `weeks` | Weeks section that encapsulate all the days of the month. | `null` |
| `weeksVerticalDivider` | 	Vertical divider that appears in the weeks section when calendar is double paned. This style overrides `verticalDivider` for the weeks section. | `null` |
| `dayCell` | Day cell that contains day content and any associated attributes. | `null` |
| `dayCellNotInMonth` | When a day does not lie in the month on which it is displayed (belongs to previous or next month), this style is merged with `dayCell`. | `{ opacity: 0.4 }` |
| `dayContent` | Content area within the day cell that contains the day of the month number. | `null` |
| `dayContentHover` |	When day content is hovered, this style is merged with `dayContent`. | `null` |
| `dayPopoverContent` | Popover container for attribute popover labels and slot content. | `{ color: '#333333', fontSize: '.8rem', whiteSpace: 'nowrap' }` |
| `dots` | Container for dot indicators. | `null` |
| `bars` | Container for bar indicators. | `null` |

---

## Date Patterns

| Property | Type | Description | Range |
| --- | --- | --- | --- |
| `days` | Number, Array | Day number from the start or end of the month. | 1 to 31, -1 to -31 |
| `weekdays` | Number, Array | Day of the week. | 1: Sun to 7: Sat |
| `ordinalWeekdays` | Object (key: Number / value: Number, Array) | Weekday ordinal position from the start or end of the month. | key: 1 to 6, -1 to -6 / value: 1: Sun to 7: Sat |
| `weeks` | Number, Array | Week number from the start or end of the month. | 1 to 6, -1 to -6 |
| `months` | Number, Array | Months of the year. | 1 to 12 |
| `years` | Number, Array | Year numbers. | 4-digit integer |
| `dailyInterval` | Number | Interval number of days from the start date (or today when no start date provided). | n > 0 |
| `weeklyInterval` | Number | Interval number of weeks from the start date (or today). | n > 0 |
| `monthlyInterval` | Number | Interval number of months from the start date (or today). | n > 0 |
| `yearlyInterval` | Number | Interval number of years from the start date (or today). | n > 0 |

---

## Calendar

### Props {#calendar-props}

| Name | Type | Description | Default |
| ---- | ---- | ----------- | ------- |
| `formats` | Object | Formats to use when display and parsing dates for various calendar sections | Reference code |
| `nav-visibility` | String | Visibility state of the navigation panel. Use `"hover"` to automatically show when title is hovered on non-touch devices or tapped on touch devices. Use `"focus"` to automatically show when title enters or leaves focus. Use `"visible"` and `"hidden"` for manual control. | `"focus"` |
| `from-page` | Object | Active page for single paned calendar or the left pane for double paned calendar. Use the `.sync` modifier for two-way binding. | `{ month: *thisMonth*, year: *thisYear* }` |
| `to-page` | Object | Active page for the right pane for double paned calendar. Use the `.sync` modifier for two-way binding. | `{ month: *nextMonth*, year: *nextMonthYear* }` |
| `min-page` | Object | Earliest page (month, year) that the user can navigate to. | `undefined` |
| `max-page` | Object | Latest page (month, year) that the user can navigate to. | `undefined` |
| `is-double-paned` | Boolean | Puts two calendars side by side. When window is constrained only a single calendar is displayed. | `false` |
| `pane-width` | Number | Width of a single pane, in pixels. | `256` |
| `is-expanded` | Boolean | Expands calendar to fill the full width of its container. | `false` |
| `theme-styles` | Object | A variety of styles that are used to customize different components of the calendar. | [Reference theme styles](#theme-styles) |
| `title-position` | String | Position of the header title (`"left"`, `"center"`, `"right"`). | `"center"` |
| `title-transition` | String | Transition type for title when navigating to a new page (`"slide-h"`, `"slide-v"`, `"fade"`, `"none"`). | `"slide-h"` |
| `weeks-transition` | String | Transition type for weeks when navigating to a new page (`"slide-h"`, `"slide-v"`, `"fade"`, `"none"`). | `"slide-h"` |
| `attributes` | Array[Object] | List of attributes to display in the calendar. | `[]` |


### Events {#calendar-events}

| Name | Description | Params |
| ---- | ----------- | ------ |
| `update:frompage` | Calendar left/single pane moved to a different page. | [`page`](#page-object) |
| `update:topage` | Calendar right pane moved to a different page. | [`page`](#page-object) |
| `dayclick` | Forwarded from the `mouseclick` event for the day content element. | [`day`](#day-object) |
| `daymouseenter` | Forwarded from the `mouseenter` event for the day content element. | [`day`](#day-object) |
| `daymouseover` | Forwarded from the `mouseover` event for the day content element. | [`day`](#day-object) |
| `daymouseleave` | Forwarded from the `mouseleave` event for the day content element. | [`day`](#day-object) |

### Slots {#calendar-slots}

| Name | Description | Props (If Scoped) |
| ---- | ----------- | ----------------- |
| `header` | Calendar header. Use slots below for specific header sections. | [`page`](#page-object) |
| `header-title` | Calendar header title. This slot is animated if `title-transition` is assigned. | [`page`](#page-object) |
| `header-left-button` | Calendar header button on the left side. | [`page`](#page-object) |
| `header-right-button` | Calendar header button on the right side.	 | [`page`](#page-object) |
| `day-popover-header` | 	If popover content is visible, this slot displays as the header. | [`day`](#day-object) |
| `day-popover-footer` | If popover content is visible, this slot displays as the footer. | [`day`](#day-object) |
| *`custom-name`* | Any number of custom named slots that are referenced by attribute popovers. | `attribute: Object`, [`day`](#day-object), `customData: Any` |

#### Page Object

| Property | Type | Description |
| -------- | ---- | ----------- |
| `month` | Number | Page month number. |
| `year` | Number | Page year number. |
| `monthLabel` | String | Page month label as specified by the `monthLabels` prop or locale settings. |
| `shortMonthLabel` | String | Shortened month label as specified by the `shortMonthLabels` prop or locale settings. |
| `yearLabel` | String | Page year label in YYYY format. |
| `shortYearLabel` | String | Page year label in YY format. |
| `monthComps` | Object | Components of the current page month. |
| `prevMonthComps` | Object | Components of the previous page month. |
| `nextMonthComps` | Object | Components of the next page page. |
| `canMove(Object) => Boolean` | Function | Function that determines if calendar can move to a desired page (due to `min-page` or `max-page` setting). |
| `move(Object)` | Function | Function that moves to the specified page. |
| `moveThisMonth()` | Function | Function that moves to the page for today's month. |
| `movePrevMonth()` | Function | Function that moves to the page for the previous month. |
| `moveNextMonth()` | Function | Function that moves to the page for the next month. |

#### Day Object

| Property | Type | Description |
| -------- | ---- | ----------- |
| `day` | Number | Day number (1 - 31). |
| `dayFromEnd` | Number | Day number from the end of the month (1 - 31). |
| `weekday` | Number | Day weekday number (1:Sun - 7:Sat). |
| `weekdayOrdinal` | Number | Weekday ordinal position from the start of the month (1 - 6). |
| `weekdayOrdinalFromEnd` | Number | Weekday ordinal position from the end of the month (1 - 6). |
| `week` | Number | Week number form the start of the month (1 - 6). |
| `weekFromEnd` | Number | Week number from the end of the month (1 - 6). |
| `month` | Number | Month number (1 - 12). |
| `year` | Number | Year number. |
| `date` | Date | Date for this day. |
| `dateTime` | Number | Result of calling `date.getTime()` for this day. |
| `inMonth` | Boolean | Day lies in the currently active month. |
| `inPrevMonth` | Boolean | Day lies in the month before the currently active month. |
| `inNextMonth` | Boolean | Day lies in the month after the currently active month. |
| `attributes` | Array | List of attributes for the day involved with the event. |
| `attributesMap` | Object | Object map of the attributes using their designated key. |
| `event` | Object | Original event that triggered the event. |

---

## Date Picker

### Props {#date-picker-props}

> Note: Accepts all props accepted by `v-calendar`

| Name | Type | Description | Default |
| ---- | ---- | ----------- | ------- |
| `value` | Date, Array[Date], Object |	Selected date, dates or date range. |	`null` |
| `mode` | String | Selection mode: `"single"`, `"multiple"`, `"range"` | `"single"` |
| `is-required` | Boolean | Prevents the **user** from clearing the selected value. Setting `value = null` still allowed through code. | `false` |
| `is-inline` | Boolean | Displays calendar inline instead of as a popover. |	`false` |
| `min-date` | Date | Minimum date selectable by the user. | `undefined` |
| `max-date` | Date | Maximum date selectable by the user. | `undefined` |
| `disabled-dates` | Array, Date, Object | Disabled dates or date range objects. | `undefined` |
| `available-dates` | Array, Date, Object | Available dates or date range objects. All other dates are disabled. | `undefined` |
| `input-props` | Object | Object with props to apply to the input element. Not applicable for inline date pickers. | [Reference code]() |
| `date-formatter` | Function | Converts a date object into text. | `date => date.toLocaleDateString()` |
| `date-parser` | Function | Function used to parse text into a date. | `text => new Date(Date.parse(text))` |
| `tint-color` | String | Background color of the selected and dragged highlighted regions (`opacity: 0.5` for dragged). This setting is overridden by `select-attribute` and `drag-attribute` if specified. | `"#66B3CC"` |
| `select-attribute` | Object | Attribute to use for the date selection in all modes. | [Reference code]() |
| `drag-attribute` | Object | Attribute to use for the dragged selection in "range" mode. | [Reference code]() |
| `show-caps` | Boolean | Show caps and the end of the highlighted and dragged regions when `mode === "range"` | `false` |
| `show-popover` | Boolean | Show popover when selected or dragged date regions are hovered. | `true` |
| `popover-expanded` | Boolean |Popover wrapper for input or slot is expanded to the full width of it's container. | `false` |
| `popover-direction` | String | Direction that popover displays relative to input or slot element: `"bottom"`, `"top"`, `"left"`, `"right"` | `"bottom"` |
| `popover-align` | String | How the popover is aligned relative to input or slot element: `"left"`, `"right"`, `"top"`, `"bottom"` | `"left"` |
| `popover-visibility` | Number | Visibility state of the popover: `"hover"`, `"focus"`, `"hidden"`, `"visible"` | `"hover"`
| `popover-content-offset` | String | Distance that the popover content is offset from the input or slot element. | `"10px"` |
| `popover-keep-visible-on-input` | Boolean | Keep the popover visible after a valid input has been selected | `false` |

### Events {#date-picker-events}

> Note: Forwards all events emmitted by `v-calendar`

| Name | Description | Params |
| ---- | ----------- | ------ |
| `input` | New date was selected. | `value: Date, Array[Date], Object` |
| `drag` | Dragged selection was updated. Only valid when `mode === "range"` | `range: Object` |

### Slots {#date-picker-slots}

| Name | Description | Props (If Scoped) |
| ---- | ----------- | ----------------- |
| *`default`* | Default slot to use as the popover anchor for v-date-picker. Most likely will contain the following custom element: `<input :value="props.inputValue" @change.native="props.updateValue($event.target.value)" />` Not applicable to inline date pickers. | `inputValue: String`, `updateValue: Function` |

---

## Attribute

| Property | Type | Description | Default |
| -------- | ---- | ----------- | ------- |
| `key` | String | Keys uniquely identify an attribute and may determine how animations are applied. | `index` |
| [`highlight`](#highlight) | Object | Highlight to associate with attribute. | `undefined` |
| [`dot`](#dot) | Object | Dot to associate with attribute. | `undefined` |
| [`bar`](#bar) | Object | Bar to associate with attribute. | `undefined` |
| [`popover`](#popover) | Object | Popover to associate with attribute. | `undefined` |
| [`contentStyle`](#content-style) | Object | Day content style to associate with the attribute. | `undefined` |
| [`contentHoverStyle`](#content-hover-style) | Object | This style is merged with the `contentStyle` property when the content is hovered. | `undefined` |
| `dates` | Date, Object, Array[Date, Object] | Date or date range objects (patterns supported) to include for the attribute. | `undefined` |
| `excludeDates` | Date, Object, Array[Date, Object] | Date or date range objects (patterns supported) to exclude. All other dates are included. | `undefined` |
| `customObject` | Any | Assign any custom data to this property for easy access within event handlers. | `undefined` |
| `order` | Number | Order that the attribute should be displayed. Higher numbers take precedence in appearance. | `0` |

### Highlight

| Property | Type | Description | Default |
| -------- | ---- | ----------- | ------- |
| `animated` | Boolean | Highlight is animated on appearing, disappearing or range change. | `true` |
| `height` | String | Height of highlighted region. | `"1.8rem"` |
| `backgroundColor` | String | Background color of highlighted region. | `"rgba(0, 0, 0, 0.5)"` |
| `borderColor` | String | Border color of highlighted region. | `undefined` |
| `borderWidth` | String | Border width of highlighted region. | `"0"` |
| `borderStyle` | String | Border style of highlighted region. | `"solid"` |
| `borderRadius` | String | Border radius of highlighted region. | `"1.8rem"` |
| `opacity` | Number | Opacity of highlighted region. | `1` |

### Dot

| Property | Type | Description | Default |
| -------- | ---- | ----------- | ------- |
| `diameter` | String | Diameter of dot. | `"5px"` |
| `backgroundColor` | String | Background color of dot. | `"rgba(0, 0, 0, 0.5)"` |
| `borderColor` | String | Border color of dot. | `undefined` |
| `borderWidth` | String | Border width of dot. | `0` |
| `borderStyle` | String | Border style of dot. | `"solid"` |
| `borderRadius` | String | Border radius of dot. | `"50%"` |
| `opacity` | Number | Opacity of dot. | `1` |

### Bar

| Property | Type | Description | Default |
| -------- | ---- | ----------- | ------- |
| `height` | String | Height of bar. | `"5px"` |
| `backgroundColor` | String | Background color of bar. | `"rgba(0, 0, 0, 0.5)"` |
| `borderColor` | String | Border color of bar. | `undefined` |
| `borderWidth` | String | Border width of bar. | `0` |
| `backgroundColor` | String | Background color of bar. | `undefined` |
| `opacity` | Number | Opacity of bar. | `1` |

### Popover

| Property | Type | Description | Default |
| -------- | ---- | ----------- | ------- |
| `label` | String, Function | Text string (or function that returns a string) to display in the popover content row. For functions, `attribute` is provided as the first parameter and the `day` is provided as the second. | `undefined` |
| `labelStyle` | Object, Function | Label style object (or function that returns an object). For functions, `attribute` is provided as the first paramter and the `day` is provided as the second. | `undefined` |
| `hideIndicator` | Boolean | Hides the indicator symbol on the left side of the popover content row. | `false` |
| `slot` | String | Name of slot to use to display the popover content row. | `undefined` |
| `visibility` | String | Visibility of the popover when this label or slot is displayed (`"hover`, `"focus"`, `"visible"`, `"hidden"`). | `"hover"` |
| `isInteractive` | Boolean | Determines if the user can interract with the popover content. If two or more popovers conflic, `true` overrides. | `false` |

### Content Style

Content hover style is just a style object. All normal style properties apply.

### Content Hover Style

Content hover style is just a style object. All normal style properties apply.