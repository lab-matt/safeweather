# Safeweather first build: layout and location

## Goal

Create a reviewable first version of the single-file `index.html` page. Focus on location selection and an hourly forecast strip. Use labeled sample weather data; defer live forecast and safety calculations.

## Build order

1. Add a persistent header with `Safeweather` at left, selected city and ZIP code in the center, and a settings drop-down control at right. Show the three planned setting labels, without assigning safety limits yet.
2. Add a full-width, 5:3 map area under the header with a centered pin and a location control in its top-right corner. Allow the user to move the map and select a point; keep the pin, selected coordinates, and header location synchronized.
3. On load, request browser location permission. If granted, center the map on that position. If denied or unavailable, use a clearly labeled default location and keep manual selection available. Resolve city and ZIP for selected coordinates when possible; display coordinates when a ZIP is unavailable.
4. Add a horizontally scrollable row of hourly cards below the map. Each card shows a local hour, abbreviated weekday, temperature, chance of rain, and average wind/gust in that order. Use several adjacent days of clearly labeled sample values so day boundaries and scrolling can be reviewed.
5. Keep layout usable on narrow screens: header contents remain readable, the map fits the viewport, and the hourly cards scroll inside their own row without making the whole page scroll sideways.

## Review checks

- Header remains visible while scrolling the page.
- Initial location, permission-denied fallback, and manually selected location are distinguishable.
- Map pin, coordinates, and city/ZIP refer to the same selected point.
- Hour labels and weekday boundaries are unambiguous; cards can be scrolled with touch, trackpad, and keyboard.
- Sample weather is identified as sample data, never as a live forecast or safety determination.

## Later passes

Connect Open-Meteo, replace sample weather with location-specific hourly data, then decide units and safety thresholds before introducing go/no-go styling, summaries, or precipitation-based colors.
