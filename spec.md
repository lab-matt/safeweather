# Jobsite Weather Planner

## Current implementation and outstanding work

The app now has a persistent Safeweather header, settings dropdown, and a 5:3 navigable map with a centered pin and selection button. It requests the user's location, falls back to Provo, and displays city and ZIP when available or coordinates otherwise. OpenStreetMap supplies the map and location lookup.

Selecting a location loads seven days of hourly Open-Meteo data in the location's time zone. The app shows the selected coordinates, time zone, retrieval time, and loading errors. Date tabs select a day, and a horizontal row displays 12-hour time, temperature in °F, rain probability, and wind speed in mph. A second horizontal row shows each day's hazard hours and affected activities.

Settings allow the user to change work hours and hazard thresholds. The ending hour is included, equal start and end times show all hours, and an end earlier than the start is rejected. Current hazard rules are rounded wind speed at or above 3 mph for crane, rain probability above 20% for roofing, and unrounded temperature below 49°F for concrete; users can adjust these thresholds. These checks are not a complete jobsite safety assessment.

Still to decide or verify: browser and mobile behavior; the intended crane rounding and equality rules; a neutral state for missing values (the current hazard summary can appear clear when data is missing); daylight saving and overnight shifts; gusts, condition colors, precipitation backgrounds, and activity summaries; and the NWS comparison and explicit exclusions. The initial design notes below include proposals that have not all been implemented and should be read alongside this current-status section.

## Purpose
Click a jobsite on a map and get a 7-day forecast showing which days are safe for the work that weather can stop: crane lifts, concrete pours, and roofing.

## Inputs
- A pin a user can place on a map to select a jobsite location.
- Jobsite activities (Crane, Concrete, Roofing) with their respective wind speed and precipitation limits.
- Open Meteo API which pulls the location’s 7-day forecast, including wind speed, precipitation, and temperature.
- Jobsite hours, so overnight weather can be excluded from the forecast.

[Note - (Specify whether users can adjust activity limits, which wind measure and units are used, and whether precipitation means probability, amount, or both.)]
[Note - (Add the jobsite time zone and define how jobsite hours, daylight saving changes, and hours crossing midnight are handled.)]
[Note - (Temperature is listed as forecast data but is not used by any activity rule; either add temperature limits for relevant work or remove it from the required forecast data.)]

## Calculations
- Compare the forecasted wind speed and precipitation against the user-defined limits for each activity.

[Note - (Define the boundary rule for values equal to a limit, how missing forecast hours are shown, and whether a day is safe only when every applicable condition passes.)]

## Outputs

An hourly forecast for the next 7 days, with each hour indicate whether the weather is safe for each activity, green for go, red for no go. A summary of safe and unsafe hours for each activity over the 7-day period.

[Note - (Define whether the 7 days are calendar days or a rolling 168 hours, and show the forecast timestamp and selected location so users can judge how current the data is.)]
[Note - (Add a neutral state for unavailable or incomplete forecast data; green/red alone could imply certainty where the app has no usable value.)]
[Note - (Clarify that the safe/unsafe result is a weather-threshold check and identify any work-specific rules the app does not evaluate.)]

## Look and feel
Very basic with minimal styling. The focus is on speed, functionality and clarity of information.

## Initial page design

- Use a persistent header at the top of the page.
- Put the product name `Safeweather` on the left side of the header.
- Center the selected jobsite's city and ZIP code in the header. By default, use the user's current location as the selected location when permission is available.
- Put a settings drop-down on the right side of the header. The drop-down will contain controls for crane wind speed, minimum chance of rain, and minimum temperature for concrete. The exact safety defaults, units, and whether these settings represent safe maximums or minimums remain to be decided.
- Below the persistent header, show the main page content.
- Begin the page content with a navigable map spanning the available screen width. The map area should use a 5:3 width-to-height aspect ratio and show the selected pin at its center.
- Style the map container as a rounded squircle. Include a location-selection control in the top-right corner of the map so the user can choose a new location. A selected location will be used to request the forecast from Open-Meteo.
- Below the map, show forecast hours as horizontally scrollable columns.
- Each day should appear as a tall rounded squircle column. Display information from top to bottom in this order: abbreviated day name (`%a`), temperature, chance of rain, and average wind speed/gust speed in the format `[average]/[gust]`.
- Render values that do not meet the applicable validation rule in red; render values that meet the rule in white. The specific validation rules and treatment of unavailable data remain to be decided.
- Use a blue-gray background gradient whose appearance changes with precipitation.

## Validation
For one location and one day, read the raw hourly forecast numbers the app downloaded, apply your thresholds by hand, and confirm the app gave the same rating. Also compare the app's forecast to the National Weather Service forecast for the same place.

|Activity|Limit|
|--------|-----|
|Crane|Wind speed < 3 mph|
|Concrete|Temperature < 49|
|Roofing|Chance of rain > 20%|

Hazard times for sat nov 28 with validation data:
9am - roofing and crane, concrete
10am - roofing, concrete
11am - roofing
2pm - crane

## Out of scope

[Note - (This section is empty; list features explicitly excluded from the first version, or remove the heading until there are exclusions to record.)]

