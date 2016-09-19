# Bootstrap Birthday Picker
Birthday picker for Bootstrap 3. It uses three select boxes to choose a date, and tries to ensure that the date is valid. It also has a number of options, making it somewhat customizable. The birthday picker (by default) generates the following markup:
```html
<div class="input-group">
  <span class="input-group-addon">
    <select name="birthday[month]" class="form-control input-sm"></select>
  </span>
  <span class="input-group-addon">
    <select name="birthday[day]" class="form-control input-sm"></select>
  </span>
  <span class="input-group-addon">
    <select name="birthday[year]" class="form-control input-sm"></select>
  </span>
</div>
```
It also adds an option list to each of the select boxes, changing the options dynamically based on plugin settings and user interactions.

## Requirements

- jQuery >= 1.9.1
- Bootstrap 3.x

## Usage

**HTML**
```html
<input type="text" name="birthday" value="" id="basic"/>
```

**JavaScript**
```javascript
$('#basic').bootstrapBirthday();
```

## Options

The following options are currently supported:

**maxAge (number)** *Default value: 120*
> The maxAge setting determines the oldest year you can pick for a birthday. So if you set the maxAge to 100 and the current year is 2010, then the oldest year you can pick will be 1910.

**minAge (number)** *Default value: 0*
> The opposite of maxAge. If current year is 2010 and minAge is set to 18, the earliest year that can be picked is 1992.

**futureDates (boolean)** *Default value: false*
> The futureDates setting determines whether birthdays in the future can be selected. Unless you need to support entering birthdays of unborn babies, this should generally be false.

**maxYear (number)** *Default value: current year*
> The maxYear setting allows you to set the maximum year that can be chosen, counting up from 0. If you pass in a year (such as 1980) then it uses that year. If you pass in a number under 1000 (such as 5) then it adds it to the current year, so if the year was 2010 then the maxYear would become 2015. If you want the maxYear to be in the future, you must set futureDates to true. If you want the maxYear in the past, you can pass in a negative number or a past year (if its over 1000).

**dateFormat (string)** *Default value: middleEndian*
> The dateFormat setting determines the order of the select fields in the markup and supports the following three values:
> - middleEndian: Month, Day, Year
> - littleEndian: Day, Month, Year
> - bigEndian: Year, Month, Day

**monthFormat (string)** *Default value: short*
> The monthFormat setting determines the text displayed in the month select box. It can be either short, or long. i.e. Jan or January

**placeholder (boolean)** *Default value: true*
> The placeholder adds a default option to each select list just like Facebook does on their signup page. The default option just says Month, Day, or Year with a colon after it. If you keep this set to true, you will need to add logic, preferably on the client and server, to ensure this option isn't chosen. The value for these options is 0.

**tabindex (number)** *Default value: null*
> The tabindex setting determines the tab order of select elements. If null, no tab index will be set.

**onChange (function)**
> Callback function to do something after birthday date changed.

## Customize widget

By default, bootstrap-birthday uses the following settings to generate HTML markup:

```javascript
$('#element').bootstrapBirthday({
  widget: {
    wrapper: {
      tag: 'div',
      class: 'input-group'
    },
    wrapperYear: {
      use: true,
      tag: 'span',
      class: 'input-group-addon'
    },
    wrapperMonth: {
      use: true,
      tag: 'span',
      class: 'input-group-addon'
    },
    wrapperDay: {
      use: true,
      tag: 'span',
      class: 'input-group-addon'
    },
    selectYear: {
      name: 'birthday[year]',
      class: 'form-control input-sm'
    },
    selectMonth: {
      name: 'birthday[month]',
      class: 'form-control input-sm'
    },
    selectDay: {
      name: 'birthday[day]',
      class: 'form-control input-sm'
    }
  }
});
```

For more examples see **test.html** file.

## Localization

Translating placeholders and month names:

```javascript
$('#element').bootstrapBirthday({
  text: {
    year: "Year",
    month: "Month",
    day: "Day",
    months: {
      short: [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec"
      ],
      long: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December"
      ]
    }
  }
});
```
