# Ember UI Calendar

#### A calendar component for Ember with a _speedy_ month view

### Rationale

HTMLBars looks very promising for template performance, but it's not with us
yet. I needed a solution to the month view problem in a light-weight Ember way
without adding redundant third-party dependencies. Existing implementations
either wrap a third-party library or take an idiomatic Ember approach, which
will be absolutely fine in the HTMLBars future, but right now it's just too
slow for my use-cases.

### Features

- Shows a month with _n_ selected days, _n_ disabled days
- Also show the previous month and future month
- Let the user move forward and backwards
- Let the user go to the current month
- Send an event when the user selects a day
- Disable moving past the current month into the future or past
- Disable user-controls in general

### Using It

_**A wild [calendar demo](http://emberjs.jsbin.com/komop/1/) appears!**_

The `ui-calendar` component wraps everything up into a widget that you can use
to display a calendar and allow you users to select one or _n_ dates:

```html
{{ui-calendar
  month=momentObject
  selectedDate=momentObject
  selectedDates=arrayOfMomentObjects
  disabledDates=arrayOfMomentObjects
  todayLabel="<span>Today</span>"
  prevLabel="<span>Raw HTML</span>"
  nextLabel="<span>Raw HTML</span>"
  showNextMonth=true|false
  showPrevMonth=true|false
  disableHeader=true|false
  disableControls=true|false
  disablePast=true|false,
  disableFuture=true|false
  disableManipulation=true|false
  maxPastDate=momentObject
  maxFutureDate=momentObject
  select="dateSelected"}}
```

| Option            | Type             | Description                           |
|:------------------|:-----------------|:--------------------------------------|
| `month`           | moment           | The explicit month to render.         |
| `selectedDate`    | moment           | Date to indicate as selected.         |
| `selectedDates`   | array of moments | Dates to indicate as selected, use this or the above, both won't work. |
| `disabledDates`   | array of moments | Dates to indicate as disabled.        |
| `todayLabel`      | HTML string      | A label to use for the Today button   |
| `prevLabel`       | HTML string      | A label to use for the previous month button |
| `nextLabel`       | HTML string      | A label to use for the next month button |
| `showNextMonth`   | boolean          | Show or hide the next month button    |
| `showPrevMonth`   | boolean          | Show or hide the previous month button |
| `disableHeader`   | boolean          | Show or hide the header               |
| `disableControls` | boolean          | Show or hide the header controls      |
| `disablePast`     | boolean          | Disable moving to past months         |
| `disableFuture`   | boolean          | Disable moving to future months       |
| `disableManipulation | boolean       | Disable built-in manipulation of `selectedDate` / `selectedDates` select action still sent |
| `maxPastDate`     | moment           | Maximum past month                    |
| `maxFutureDate`   | moment           | Maximum future month                  |
| `select`          | action name      | Will fire this event with the selected moment when the user selects a date |

The `ui-month` component is what powers the individual month views, you can use
it if you want to build your own calendar functionality:

```html
{{ui-month
  month=momentObject
  selectedDates=arrayOfMomentObjects
  disabledDates=arrayOfMomentObjects
  select="dateSelected"}}
```

### Development

Install the project dev dependencies, it will load about 50,000 microframeworks
into `node_modules`.

```sh
$ npm install
```

Then install the Bower dependencies:

```sh
$ npm install -g bower # if you don't have Bower installed on your system
$ bower install
```

After that you can run:

```sh
$ npm install -g broccoli-cli # if you don't have Broccoli CLI on your system
$ broccoli serve
```

Then either play around with one of the [examples](/examples) or fire up the
test runner and add some tests:

```sh
$ testem # Then follow the instructions
```
