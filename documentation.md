# Table of Contents
- [Calendar](#calendar)
- [Calendar.Date](#calendar-date)
- [CalendarLocale](#calendarlocale)

---

# Calendar
**Inherits:** RefCounted < Object

A utility library for generating calendar data.

## Description
Calendar is a comprehensive library for creating calendar views, including yearly, monthly, weekly overviews, and agendas. It follows Godot's Time conventions (Sunday = 0 to Saturday = 6) and uses the Proleptic Gregorian Calendar (the day before 1582-10-15 is 1582-10-14).  
Calendar works with the helper class Calendar.Date and can localize output via a CalendarLocale resource.

---

## Properties
CalendarLocale [calendar_locale](#calendar-prop-calendar_locale)  
Time.Weekday [first_weekday](#calendar-prop-first_weekday)  
WeekNumberSystem [week_number_system](#calendar-prop-week_number_system)

### Property Descriptions

#### <a id="calendar-prop-calendar_locale"></a>CalendarLocale **calendar_locale**
The calendar's localization settings for retrieving preformatted values. Each calendar is assigned a CalendarLocale, defaulting to English. Assign a custom resource to localize names and formats.  
See [CalendarLocale](#calendarlocale).

#### <a id="calendar-prop-first_weekday"></a>Time.Weekday **first_weekday**
The weekday considered the first day of the week. Uses Time.Weekday where Sunday = 0 and Saturday = 6.

#### <a id="calendar-prop-week_number_system"></a>WeekNumberSystem **week_number_system**
Which system to use when calculating week numbers. See [WeekNumberSystem](#calendar-enumerations).

---

## Methods
Array [get_calendar_month(year: int, month: int, include_adjacent_days: bool = false, force_six_weeks: bool = false)](#calendar-method-get_calendar_month)  
Array\[Date] [get_calendar_week(year: int, month: int, day: int, days_in_week: int = 7)](#calendar-method-get_calendar_week)  
Array [get_calendar_year(year: int, include_adjacent_days: bool = false, force_six_weeks: bool = true)](#calendar-method-get_calendar_year)  
String [get_date_formatted(year: int, month: int, day: int, format: String = '%Y-%m-%d')](#calendar-method-get_date_formatted)  
String [get_date_locale_format(year: int, month: int, day: int, four_digit_year: bool = true)](#calendar-method-get_date_locale_format)  
int [get_day_of_year(year: int, month: int, day: int)](#calendar-method-get_day_of_year)  
int [get_days_in_month(year: int, month: int)](#calendar-method-get_days_in_month)  
int [get_days_in_year(year: int)](#calendar-method-get_days_in_year)  
Array\[Date] [get_days_of_range(days: int, year: int, month: int, day: int, exclusive: bool = false)](#calendar-method-get_days_of_range)  
int [get_leap_days(from_year: int, to_year: int, exclusive_to: bool = true)](#calendar-method-get_leap_days)  
String [get_month_formatted(month: int, month_format: MonthFormat = 1)](#calendar-method-get_month_formatted)  
Array\[String] [get_months_formatted(month_format: MonthFormat = 1)](#calendar-method-get_months_formatted)  
Date [get_today()](#calendar-method-get_today)  
int [get_week_number(year: int, month: int, day: int)](#calendar-method-get_week_number)  
Time.Weekday [get_weekday(year: int, month: int, day: int)](#calendar-method-get_weekday)  
String [get_weekday_formatted(year: int, month: int, day: int, weekday_format: WeekdayFormat = 0)](#calendar-method-get_weekday_formatted)  
Array\[Time.Weekday] [get_weekdays()](#calendar-method-get_weekdays)  
Array\[String] [get_weekdays_formatted(weekday_format: WeekdayFormat = 1)](#calendar-method-get_weekdays_formatted)  
Array\[int] [get_weeks_of_month(year: int, month: int, force_six_weeks: bool = false)](#calendar-method-get_weeks_of_month)  
bool [is_leap_year(year: int)](#calendar-method-is_leap_year)  
void [set_calendar_locale(path: String)](#calendar-method-set_calendar_locale)  
void [set_first_weekday(first_weekday: Time.Weekday)](#calendar-method-set_first_weekday)  
void [set_week_number_system(week_number_system: WeekNumberSystem)](#calendar-method-set_week_number_system)

### Method Descriptions

#### <a id="calendar-method-get_calendar_month"></a>Array **get_calendar_month(year: int, month: int, include_adjacent_days: bool = false, force_six_weeks: bool = false)**  
Returns an array of weeks, where each week is an array of Date objects for the given month.  
include_adjacent_days includes days from the previous/next month in the outer weeks; otherwise those slots are 0.  
force_six_weeks ensures the month is represented using six weeks for consistent grid layouts.

#### <a id="calendar-method-get_calendar_week"></a>Array\[Date] **get_calendar_week(year: int, month: int, day: int, days_in_week: int = 7)**  
Returns a Date array for the week that contains the given date. days_in_week can be shorter (for workweeks, etc.).

#### <a id="calendar-method-get_calendar_year"></a>Array **get_calendar_year(year: int, include_adjacent_days: bool = false, force_six_weeks: bool = true)**  
Returns an array of months for the year. Each month is an array of weeks of Date objects.  
include_adjacent_days and force_six_weeks behave like in get_calendar_month.

#### <a id="calendar-method-get_date_formatted"></a>String **get_date_formatted(year: int, month: int, day: int, format: String = '%Y-%m-%d')**  
Returns a formatted string for the given date using a POSIX-like pattern. Supported placeholders include:  
%Y four-digit year, %y two-digit year, %-y two-digit no pad, %m zero-padded month, %-m month, %d zero-padded day, %-d day, %F ISO8601 date, %B/%b/%-b month names via CalendarLocale, %A/%a/%-a weekday names via CalendarLocale, %j/%-j day of year, %u ISO weekday (Mon=1), %w weekday (Sun=0).

#### <a id="calendar-method-get_date_locale_format"></a>String **get_date_locale_format(year: int, month: int, day: int, four_digit_year: bool = true)**  
Formats the date using the active CalendarLocale's date_format and divider_symbol.  
See [CalendarLocale](#calendarlocale).

#### <a id="calendar-method-get_day_of_year"></a>int **get_day_of_year(year: int, month: int, day: int)**  
Returns the ordinal day index of the year.

#### <a id="calendar-method-get_days_in_month"></a>int **get_days_in_month(year: int, month: int)**  
Returns the number of days in the given month. February returns 29 in leap years.

#### <a id="calendar-method-get_days_in_year"></a>int **get_days_in_year(year: int)**  
Returns 365 or 366 depending on leap year status.

#### <a id="calendar-method-get_days_of_range"></a>Array\[Date] **get_days_of_range(days: int, year: int, month: int, day: int, exclusive: bool = false)**  
Returns a sequence of Date objects spanning days, starting from the given date.  
If exclusive is true, the last day is included in the range length.

#### <a id="calendar-method-get_leap_days"></a>int **get_leap_days(from_year: int, to_year: int, exclusive_to: bool = true)**  
Returns the number of leap days between from_year and to_year. If exclusive_to is false, includes to_year.

#### <a id="calendar-method-get_month_formatted"></a>String **get_month_formatted(month: int, month_format: MonthFormat = 1)**  
Returns the localized month name for month (1–12), formatted per MonthFormat.  
See [MonthFormat](#calendar-enumerations) and [CalendarLocale](#calendarlocale).

#### <a id="calendar-method-get_months_formatted"></a>Array\[String] **get_months_formatted(month_format: MonthFormat = 1)**  
Returns all month names in order using month_format.

#### <a id="calendar-method-get_today"></a>Date **get_today()**  
Returns the current date as a Calendar.Date.

#### <a id="calendar-method-get_week_number"></a>int **get_week_number(year: int, month: int, day: int)**  
Returns the week number for the given date, using the configured week_number_system.  
See [WeekNumberSystem](#calendar-enumerations).

#### <a id="calendar-method-get_weekday"></a>Time.Weekday **get_weekday(year: int, month: int, day: int)**  
Returns the weekday for the date (Sunday = 0 ... Saturday = 6).

#### <a id="calendar-method-get_weekday_formatted"></a>String **get_weekday_formatted(year: int, month: int, day: int, weekday_format: WeekdayFormat = 0)**  
Returns the localized weekday name using weekday_format.  
See [WeekdayFormat](#calendar-enumerations) and [CalendarLocale](#calendarlocale).

#### <a id="calendar-method-get_weekdays"></a>Array\[Time.Weekday] **get_weekdays()**  
Returns all weekdays starting from first_weekday.

#### <a id="calendar-method-get_weekdays_formatted"></a>Array\[String] **get_weekdays_formatted(weekday_format: WeekdayFormat = 1)**  
Returns weekday names starting at first_weekday, formatted by weekday_format.

#### <a id="calendar-method-get_weeks_of_month"></a>Array\[int] **get_weeks_of_month(year: int, month: int, force_six_weeks: bool = false)**  
Returns all week numbers present in the month.  
force_six_weeks ensures a six-row layout alignment across months.

#### <a id="calendar-method-is_leap_year"></a>bool **is_leap_year(year: int)**  
Returns whether year is a leap year.

#### <a id="calendar-method-set_calendar_locale"></a>void **set_calendar_locale(path: String)**  
Assigns a CalendarLocale resource to the calendar.

#### <a id="calendar-method-set_first_weekday"></a>void **set_first_weekday(first_weekday: Time.Weekday)**  
Sets the first day of the week for the calendar.

#### <a id="calendar-method-set_week_number_system"></a>void **set_week_number_system(week_number_system: WeekNumberSystem)**  
Sets the week numbering system. See [WeekNumberSystem](#calendar-enumerations).

---

## Enumerations
### <a id="calendar-enumerations"></a>WeekdayFormat
WEEKDAY_FORMAT_FULL = 0 — Full name  
WEEKDAY_FORMAT_ABBR = 1 — Abbreviated (e.g. 'Mon')  
WEEKDAY_FORMAT_SHORT = 2 — Short (e.g. 'M')

### MonthFormat
MONTH_FORMAT_FULL = 0 — Full month name  
MONTH_FORMAT_ABBR = 1 — Abbreviated (e.g. 'Jan')  
MONTH_FORMAT_SHORT = 2 — Short (e.g. 'J')

### WeekNumberSystem
WEEK_NUMBER_FOUR_DAY = 0 — First week has at least four days (respects first_weekday)  
WEEK_NUMBER_TRADITIONAL = 1 — First week is the one containing January 1

---

# Calendar.Date
**Inherits:** RefCounted < Object

A utility class for storing and handling dates.

## Description
Calendar.Date holds a specific date: year, month, and day. It is used throughout Calendar wherever full date information is required.

---

## Properties
int [day](#date-prop-day)  
int [month](#date-prop-month)  
int [year](#date-prop-year)

### Property Descriptions

#### <a id="date-prop-day"></a>int **day**
The day of this date. Valid range: 1–31 (depending on month).

#### <a id="date-prop-month"></a>int **month**
The month of this date. 1–12 representing January–December.

#### <a id="date-prop-year"></a>int **year**
The year of this date.

---

## Methods
void [add_days(days: int)](#date-method-add_days)  
void [add_months(months: int)](#date-method-add_months)  
void [add_years(years: int)](#date-method-add_years)  
int [days_to(date: Date)](#date-method-days_to)  
Date [duplicate()](#date-method-duplicate)  
void [from_dict(date: Dictionary)](#date-method-from_dict)  
int [get_day_of_year()](#date-method-get_day_of_year)  
Time.Weekday [get_weekday()](#date-method-get_weekday)  
int [get_weekday_iso()](#date-method-get_weekday_iso)  
bool [is_after(date: Date)](#date-method-is_after)  
bool [is_before(date: Date)](#date-method-is_before)  
bool [is_equal(date: Date)](#date-method-is_equal)  
bool [is_leap_year()](#date-method-is_leap_year)  
bool [is_valid()](#date-method-is_valid)  
void [set_date(year: int, month: int, day: int)](#date-method-set_date)  
void [set_today()](#date-method-set_today)  
void [subtract_days(days: int)](#date-method-subtract_days)  
void [subtract_months(months: int)](#date-method-subtract_months)  
void [subtract_years(years: int)](#date-method-subtract_years)  
Date [today() static](#date-method-today)

### Method Descriptions

#### <a id="date-method-add_days"></a>void **add_days(days: int)**  
Adds days to this date.

#### <a id="date-method-add_months"></a>void **add_months(months: int)**  
Adds months to this date. If the target month has fewer days, the day is clamped to the month's last valid day. February 29 becomes February 28 in non-leap years.

#### <a id="date-method-add_years"></a>void **add_years(years: int)**  
Adds years to this date. February 29 becomes February 28 if the resulting year is not a leap year.

#### <a id="date-method-days_to"></a>int **days_to(date: Date)**  
Returns the number of days between this date and date. Accurate for dates after 1582.

#### <a id="date-method-duplicate"></a>Date **duplicate()**  
Returns a new Date copy of this date.

#### <a id="date-method-from_dict"></a>void **from_dict(date: Dictionary)**  
Sets this date from a dictionary containing year, month, and day. Intended to convert dictionaries returned by Time.

#### <a id="date-method-get_day_of_year"></a>int **get_day_of_year()**  
Returns the ordinal day index of the year.

#### <a id="date-method-get_weekday"></a>Time.Weekday **get_weekday()**  
Returns the weekday (Sunday = 0 ... Saturday = 6).

#### <a id="date-method-get_weekday_iso"></a>int **get_weekday_iso()**  
Returns ISO weekday number (Monday = 1 ... Sunday = 7).

#### <a id="date-method-is_after"></a>bool **is_after(date: Date)**  
Returns true if this date is after date.

#### <a id="date-method-is_before"></a>bool **is_before(date: Date)**  
Returns true if this date is before date.

#### <a id="date-method-is_equal"></a>bool **is_equal(date: Date)**  
Returns true if this date is equal to date.

#### <a id="date-method-is_leap_year"></a>bool **is_leap_year()**  
Returns whether this date's year is a leap year.

#### <a id="date-method-is_valid"></a>bool **is_valid()**  
Returns whether this date is a valid calendar date.

#### <a id="date-method-set_date"></a>void **set_date(year: int, month: int, day: int)**  
Sets the year, month, and day. Errors if the date is invalid.

#### <a id="date-method-set_today"></a>void **set_today()**  
Sets this date to today's system date.

#### <a id="date-method-subtract_days"></a>void **subtract_days(days: int)**  
Subtracts days from this date.

#### <a id="date-method-subtract_months"></a>void **subtract_months(months: int)**  
Subtracts months from this date. If the target month has fewer days, the day is clamped to the month's last valid day. February 29 becomes February 28 in non-leap years.

#### <a id="date-method-subtract_years"></a>void **subtract_years(years: int)**  
Subtracts years from this date. February 29 becomes February 28 if the resulting year is not a leap year.

#### <a id="date-method-today"></a>Date **today() static**  
Returns a new Date set to today's system date.

---

# CalendarLocale
**Inherits:** Resource < RefCounted < Object

A resource to define localized names for weekdays and months.

## Description
CalendarLocale is used by Calendar to provide localized weekday and month names and formatting. Create and assign a CalendarLocale to a Calendar to localize output.

---

## Properties

### Month Names (full)
String [january](#locale-prop-january)  
String [february](#locale-prop-february)  
String [march](#locale-prop-march)  
String [april](#locale-prop-april)  
String [may](#locale-prop-may)  
String [june](#locale-prop-june)  
String [july](#locale-prop-july)  
String [august](#locale-prop-august)  
String [september](#locale-prop-september)  
String [october](#locale-prop-october)  
String [november](#locale-prop-november)  
String [december](#locale-prop-december)

### Month Names (abbreviated)
String [abbr_january](#locale-prop-abbr_january)  
String [abbr_february](#locale-prop-abbr_february)  
String [abbr_march](#locale-prop-abbr_march)  
String [abbr_april](#locale-prop-abbr_april)  
String [abbr_may](#locale-prop-abbr_may)  
String [abbr_june](#locale-prop-abbr_june)  
String [abbr_july](#locale-prop-abbr_july)  
String [abbr_august](#locale-prop-abbr_august)  
String [abbr_september](#locale-prop-abbr_september)  
String [abbr_october](#locale-prop-abbr_october)  
String [abbr_november](#locale-prop-abbr_november)  
String [abbr_december](#locale-prop-abbr_december)

### Month Names (short)
String [short_january](#locale-prop-short_january)  
String [short_february](#locale-prop-short_february)  
String [short_march](#locale-prop-short_march)  
String [short_april](#locale-prop-short_april)  
String [short_may](#locale-prop-short_may)  
String [short_june](#locale-prop-short_june)  
String [short_july](#locale-prop-short_july)  
String [short_august](#locale-prop-short_august)  
String [short_september](#locale-prop-short_september)  
String [short_october](#locale-prop-short_october)  
String [short_november](#locale-prop-short_november)  
String [short_december](#locale-prop-short_december)

### Weekday Names (full)
String [sunday](#locale-prop-sunday)  
String [monday](#locale-prop-monday)  
String [tuesday](#locale-prop-tuesday)  
String [wednesday](#locale-prop-wednesday)  
String [thursday](#locale-prop-thursday)  
String [friday](#locale-prop-friday)  
String [saturday](#locale-prop-saturday)

### Weekday Names (abbreviated)
String [abbr_sunday](#locale-prop-abbr_sunday)  
String [abbr_monday](#locale-prop-abbr_monday)  
String [abbr_tuesday](#locale-prop-abbr_tuesday)  
String [abbr_wednesday](#locale-prop-abbr_wednesday)  
String [abbr_thursday](#locale-prop-abbr_thursday)  
String [abbr_friday](#locale-prop-abbr_friday)  
String [abbr_saturday](#locale-prop-abbr_saturday)

### Weekday Names (short)
String [short_sunday](#locale-prop-short_sunday)  
String [short_monday](#locale-prop-short_monday)  
String [short_tuesday](#locale-prop-short_tuesday)  
String [short_wednesday](#locale-prop-short_wednesday)  
String [short_thursday](#locale-prop-short_thursday)  
String [short_friday](#locale-prop-short_friday)  
String [short_saturday](#locale-prop-short_saturday)

### Formatting Settings
int [date_format](#locale-prop-date_format)  
String [divider_symbol](#locale-prop-divider_symbol)

---

## Property Descriptions

### Month Names (full)

#### <a id="locale-prop-january"></a>String **january** \[default: 'January']  
There is currently no description for this property.

#### <a id="locale-prop-february"></a>String **february** \[default: 'February']  
There is currently no description for this property.

#### <a id="locale-prop-march"></a>String **march** \[default: 'March']  
There is currently no description for this property.

#### <a id="locale-prop-april"></a>String **april** \[default: 'April']  
There is currently no description for this property.

#### <a id="locale-prop-may"></a>String **may** \[default: 'May']  
There is currently no description for this property.

#### <a id="locale-prop-june"></a>String **june** \[default: 'June']  
There is currently no description for this property.

#### <a id="locale-prop-july"></a>String **july** \[default: 'July']  
There is currently no description for this property.

#### <a id="locale-prop-august"></a>String **august** \[default: 'August']  
There is currently no description for this property.

#### <a id="locale-prop-september"></a>String **september** \[default: 'September']  
There is currently no description for this property.

#### <a id="locale-prop-october"></a>String **october** \[default: 'October']  
There is currently no description for this property.

#### <a id="locale-prop-november"></a>String **november** \[default: 'November']  
There is currently no description for this property.

#### <a id="locale-prop-december"></a>String **december** \[default: 'December']  
There is currently no description for this property.

### Month Names (abbreviated)

#### <a id="locale-prop-abbr_january"></a>String **abbr_january** \[default: 'Jan']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_february"></a>String **abbr_february** \[default: 'Feb']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_march"></a>String **abbr_march** \[default: 'Mar']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_april"></a>String **abbr_april** \[default: 'Apr']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_may"></a>String **abbr_may** \[default: 'May']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_june"></a>String **abbr_june** \[default: 'Jun']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_july"></a>String **abbr_july** \[default: 'Jul']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_august"></a>String **abbr_august** \[default: 'Aug']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_september"></a>String **abbr_september** \[default: 'Sep']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_october"></a>String **abbr_october** \[default: 'Oct']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_november"></a>String **abbr_november** \[default: 'Nov']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_december"></a>String **abbr_december** \[default: 'Dec']  
There is currently no description for this property.

### Month Names (short)

#### <a id="locale-prop-short_january"></a>String **short_january** \[default: 'J']  
There is currently no description for this property.

#### <a id="locale-prop-short_february"></a>String **short_february** \[default: 'F']  
There is currently no description for this property.

#### <a id="locale-prop-short_march"></a>String **short_march** \[default: 'M']  
There is currently no description for this property.

#### <a id="locale-prop-short_april"></a>String **short_april** \[default: 'A']  
There is currently no description for this property.

#### <a id="locale-prop-short_may"></a>String **short_may** \[default: 'M']  
There is currently no description for this property.

#### <a id="locale-prop-short_june"></a>String **short_june** \[default: 'J']  
There is currently no description for this property.

#### <a id="locale-prop-short_july"></a>String **short_july** \[default: 'J']  
There is currently no description for this property.

#### <a id="locale-prop-short_august"></a>String **short_august** \[default: 'A']  
There is currently no description for this property.

#### <a id="locale-prop-short_september"></a>String **short_september** \[default: 'S']  
There is currently no description for this property.

#### <a id="locale-prop-short_october"></a>String **short_october** \[default: 'O']  
There is currently no description for this property.

#### <a id="locale-prop-short_november"></a>String **short_november** \[default: 'N']  
There is currently no description for this property.

#### <a id="locale-prop-short_december"></a>String **short_december** \[default: 'D']  
There is currently no description for this property.

### Weekday Names (full)

#### <a id="locale-prop-sunday"></a>String **sunday** \[default: 'Sunday']  
There is currently no description for this property.

#### <a id="locale-prop-monday"></a>String **monday** \[default: 'Monday']  
There is currently no description for this property.

#### <a id="locale-prop-tuesday"></a>String **tuesday** \[default: 'Tuesday']  
There is currently no description for this property.

#### <a id="locale-prop-wednesday"></a>String **wednesday** \[default: 'Wednesday']  
There is currently no description for this property.

#### <a id="locale-prop-thursday"></a>String **thursday** \[default: 'Thursday']  
There is currently no description for this property.

#### <a id="locale-prop-friday"></a>String **friday** \[default: 'Friday']  
There is currently no description for this property.

#### <a id="locale-prop-saturday"></a>String **saturday** \[default: 'Saturday']  
There is currently no description for this property.

### Weekday Names (abbreviated)

#### <a id="locale-prop-abbr_sunday"></a>String **abbr_sunday** \[default: 'Sun']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_monday"></a>String **abbr_monday** \[default: 'Mon']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_tuesday"></a>String **abbr_tuesday** \[default: 'Tue']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_wednesday"></a>String **abbr_wednesday** \[default: 'Wed']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_thursday"></a>String **abbr_thursday** \[default: 'Thu']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_friday"></a>String **abbr_friday** \[default: 'Fri']  
There is currently no description for this property.

#### <a id="locale-prop-abbr_saturday"></a>String **abbr_saturday** \[default: 'Sat']  
There is currently no description for this property.

### Weekday Names (short)

#### <a id="locale-prop-short_sunday"></a>String **short_sunday** \[default: 'S']  
There is currently no description for this property.

#### <a id="locale-prop-short_monday"></a>String **short_monday** \[default: 'M']  
There is currently no description for this property.

#### <a id="locale-prop-short_tuesday"></a>String **short_tuesday** \[default: 'T']  
There is currently no description for this property.

#### <a id="locale-prop-short_wednesday"></a>String **short_wednesday** \[default: 'W']  
There is currently no description for this property.

#### <a id="locale-prop-short_thursday"></a>String **short_thursday** \[default: 'T']  
There is currently no description for this property.

#### <a id="locale-prop-short_friday"></a>String **short_friday** \[default: 'F']  
There is currently no description for this property.

#### <a id="locale-prop-short_saturday"></a>String **short_saturday** \[default: 'S']  
There is currently no description for this property.

### Formatting Settings

#### <a id="locale-prop-date_format"></a>int **date_format** \[default: 0]  
The standard date format for the locale. Use Calendar.get_date_locale_format() to format dates.

#### <a id="locale-prop-divider_symbol"></a>String **divider_symbol** \[default: '-']  
Symbol dividing year, month, and day in the locale's date format, e.g. Y/M/D or D-M-Y.

---
