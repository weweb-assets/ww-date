---
name: ww-date
description: The ww-date component utilizes the dayjs library to display a specified date in a chosen or custom format, offering flexibility in date presentation through predefined or user-defined formats.
keywords:
  - dayjs
  - date formatting
  - iso string
  - custom format
  - predefined format
  - ww-text
  - component properties
  - formatted date
  - javascript library
  - web component
---

#### ww-date

Displays a formatted date using the dayjs library. Specify date and format.

Properties:
- date: string - ISO string date (e.g., "2021-03-11T10:11:20.000+00:00"). Default: "2021-03-11T10:11:20.000+00:00"
- format: 'DD/MM/YYYY' | 'MMMM D, YYYY' | 'MMM D, YYYY' | 'h:mm A' | 'h:mm:ss A' | 'MMM D, YYYY h:mm A' | 'ddd, MMM D, YYYY h:mm A' - Predefined format. Default: "DD/MM/YYYY"
- customFormat: string - Custom format (e.g., "MMMM D, YYYY h:mm A"). Default: ""

Children:
- el: ww-text - Displays the formatted date

Special Features:
- Uses dayjs library for date formatting
- doc property opens dayjs documentation in new tab (editor-only)

Events: none

Variables: none
