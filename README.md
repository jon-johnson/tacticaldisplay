# M32 Tactical Tool

A lightweight browser-based **tactical live and replay tool for
sailing races** using **Vakaros RaceSense telemetry**.

This tool allows sailors and coaches to replay race sessions, visualize
course geometry, and extract key tactical metrics such as **start line
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

## Replay Mode

Replay historical RaceSense events using a timeline scrubber.

This allows analysis of:

-   pre‑start positioning
-   mark drift
-   wind shifts
-   course adjustments during the day

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

## RaceSense Event ID

Example:

    IyYGkmRTu1vTOXMXlA6Y

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

Multiple serials may be entered separated by commas.

------------------------------------------------------------------------

## Gun Times

Race start times must be entered in **Unix milliseconds**.

Example:

    1,1763571840000
    2,1763573640000
    3,1763575440000

Format:

    raceNumber,unixTimestamp

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
