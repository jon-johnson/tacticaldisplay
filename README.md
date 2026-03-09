# M32 Tactical Tool

A lightweight browser-based **tactical live and replay tool for
sailing races** using **Vakaros RaceSense telemetry**.

This tool's purpose is to  sailors and coaches to get live data from a race sense viewer and utilise this for making decisions. It should also have functionality to replay race sessions, visualize course geometry.  
The key tactical metrics are **start line
bias, gate bias, and optimal start positions**.

The entire application runs from a **single HTML file** with **no
backend required**.

------------------------------------------------------------------------

# Project Goals

The purpose of this tool is to provide **fast tactical insight from race
telemetry** without requiring heavy software.

It focuses on:

-   extracting geometry from RaceSense telemetry
-   visualizing race course structure
-   presenting tactical metrics clearly on mobile devices
-   enabling replay analysis for race coaching

The system intentionally **shows numbers rather than advice**, allowing
sailors and coaches to interpret the results themselves.

------------------------------------------------------------------------

# Key Features

## Live Mode

Pull live data from Vakaros Race Sense link and turn it into a dashboard with key tactical metrics, including:

- course axis between windward and leeward gates
- gate axises, and biases relative to wind or course axis in the gates
- Start line geometry (distance from pin, distance from RC, difference)
- Optimal starting position based on wind direction/course axis
- Other metrics to be defined later

## Replay Mode

Replay historical RaceSense events using a timeline scrubber, showing the same essential metrics.

The replay slider moves through time while loading telemetry around the
selected moment.

Typical telemetry window:

    cursorTime - 120 seconds
    cursorTime + 30 seconds

This provides enough data to reconstruct boat tracks and detect marks.

------------------------------------------------------------------------

## Tactical Metrics

The tool calculates key metrics used in high‑performance fleet racing.

### Optimal Start Line Position

Determines the best location on the start line based on:

-   wind direction
-   reach mark geometry
-   start line axis

Displayed as distance from:

-   pin end
-   RC boat

------------------------------------------------------------------------

### WL Gate Bias

Bias of the **leeward gate** relative to the wind axis.

Displayed in meters indicating which side is favoured.

------------------------------------------------------------------------

### Start Line Geometry

Shows:

-   distance from **pin → reach mark**
-   distance from **RC → reach mark**
-   difference between the two

This reveals geometric bias of the start line.

------------------------------------------------------------------------

### Reach Leg TWA

True wind angle from the **midpoint of the start line to the reach
mark**.

Useful for understanding likely reach angles after the start.

------------------------------------------------------------------------

### Start Line Optimal Position

Combines true wind angle and the polars from the World Championships race report document to estimate an optimal starting position.

Useful for identifying where to start on the line

------------------------------------------------------------------------

### WW Gate Bias

Bias of the **windward gate** relative to the wind axis.

------------------------------------------------------------------------

### Course & Gate Axes

Displays:

-   course axis
-   gate axis
-   start line axis

These provide context for the tactical calculations.

------------------------------------------------------------------------

### Wind Direction and Strength

User can manually enter a wind direction and strength to use as a baseline for the metrics to load.

------------------------------------------------------------------------

# Course Visualization

The course map displays:

-   RC boat
-   pin end
-   windward gate
-   leeward gate
-   reach mark

The visualization is oriented so that the **windward gate is always at
the top of the map**.

Example layout:

                WW Gate
                   ▲
                   |
                   |
            Reach Mark
                   |
                   |
    Pin -------------------- RC
                   |
                   |
                WL Gate

This orientation matches how sailors typically visualize the course.

------------------------------------------------------------------------

# Mobile‑First Data Layout

The **Data page** is optimized for phone viewing during debriefs.

Information hierarchy:

1.  Optimal start position
2.  WL gate bias
3.  Start line geometry
4.  Reach mark TWA
5.  WW gate bias
6.  Course axes

Each metric appears as a **large readable card**.

------------------------------------------------------------------------

# Setup

When the tool loads, you must configure the event.

## RaceSense Event URL

Example:

    (https://vakaros-racesense.web.app/watch/zRN8bknazFs5ecld7QIo/M32?race-day=3)

------------------------------------------------------------------------

## Event Timezone

Ensures replay times match the **event location** instead of the
viewer's browser timezone.

Example:

    UTC-5

------------------------------------------------------------------------

## Mark Serial Numbers

Each physical mark and committee boat broadcasts a **unique serial
identifier**.

Required:

    RC boat serial
    Pin serial
    WW gate serials
    WL gate serials

Multiple serials may be entered separated by commas. Default for these should be taken from the serial numbers in the World Championships race report

------------------------------------------------------------------------

## Gun Times

Race start times must be entered in **Dateandtime**.

Example:

    1,21/11/25, 12:04:00

Format:

    raceNumber,dateandtime

------------------------------------------------------------------------

# Reach Mark Adjustment

If telemetry does not provide a reliable reach mark location, it can be
**manually adjusted by tapping the map**.

This allows correction for:

-   missing marks
-   incorrect mark detection
-   reach mark repositioning between races

------------------------------------------------------------------------

# Detecting Mark Serial Numbers

RaceSense telemetry includes mark serial identifiers.

When data is loaded the tool displays **detected serial numbers** so
they can easily be copied into the configuration fields.

Detect the mark serial numbers from the World Championships race report as default

------------------------------------------------------------------------

# Running the Tool

No installation required.

Open the HTML file directly in a browser.

Recommended browsers:

-   Chrome
-   Safari
-   Edge

Compatible with:

-   desktop
-   tablet
-   mobile

------------------------------------------------------------------------

# Architecture

The application is intentionally simple.

    HTML UI
       │
       ├── RaceSense API requests
       │
       ├── Telemetry parser
       │
       ├── Geometry engine
       │
       └── Tactical metrics calculator

Everything runs client‑side.

------------------------------------------------------------------------

# Intended Users

-   professional sailing teams
-   race coaches
-   performance analysts
-   high‑level dinghy and keelboat fleets

------------------------------------------------------------------------

# Future Development

Planned improvements:

-   automatic gun time detection
-   automatic mark serial discovery
-   replay animation mode
-   race‑by‑race timeline
-   improved wind inference
-   start line tactical overlay
-   faster telemetry caching
-   event presets

------------------------------------------------------------------------

# Known Limitations

-   requires valid RaceSense telemetry
-   mark serial numbers may require manual entry
-   wind direction is inferred and may contain noise
-   replay performance depends on telemetry availability

------------------------------------------------------------------------

# License

This project is currently intended for **internal team use and
development**.
