# 3D Vessel Biofouling Digital Twin

This project is a prototype for showing biofouling on a ship hull using a 3D digital twin.

The main idea is : an AI model can detect biofouling from  data gathered By diver or ROV, then the result can be displayed on a 3D model of the vessel. This helps Asset owners understand where fouling exists, how severe it is, and which parts of the hull may need cleaning or maintenance.

# What This Demo Shows?


It shows:

- A 3D vessel model built with Three.js.
- Colored hull zones that represent biofouling severity.
- A legend for clean, light, moderate, and heavy fouling.
- A zone inspector panel that shows details when the user hovers over a hull area.
- Fouling data such as thickness, density, classification, and estimated speed loss.
- View controls for draft level, hull opacity, auto rotation, waterline X-ray, and camera reset.
- Animated water and vessel movement to make the scene feel more realistic.

# Project Goal

The goal of this work is to support hull inspection and maintenance decisions.

Instead of only showing AI detection results as numbers or images, the system converts the results into a visual 3D map. This makes it easier for engineers, ship operators, and inspectors to see the real condition of the vessel.

# How It Works

The prototype uses sample fouling data inside the HTML file.

Each hull zone has:

- Zone name
- Fouling thickness in millimeters
- Fouling density
- Region on the vessel
- Fouling classification

The classification logic uses thickness and density values to decide the fouling level:

- `Clean`
- `Light`
- `Moderate`
- `Heavy`

After classification, the hull is colored based on the severity. Green means clean or light fouling, orange means moderate fouling, and red means heavy fouling.

# Main Hull Zones

The demo includes several important vessel areas:

- Flat bottom
- Port bilge keel
- Starboard bilge keel
- Bow bulb
- Stern underwater area
- Propeller
- Rudder
- Port sea chest
- Starboard sea chest
- Boot top band
- Topsides above the waterline

These zones are useful because biofouling does not grow equally everywhere. Areas like the flat bottom, sea chests, propeller, rudder, and bow bulb can have different fouling patterns and different maintenance priority.

# How To Run

Open the file in a web browser:

```text
vessel-3d-fouling.html
```

The demo uses Three.js from a CDN, so an internet connection may be needed the first time the file is opened.

No build step is required. There is no need to install Node.js or run a server for the current version.

# How To Use

Use the mouse to interact with the vessel:

- Drag to rotate the 3D view.
- Scroll to zoom in or out.
- Hover over colored hull areas to inspect fouling details.

Use the control panel to:

- Change the draft level.
- Adjust hull opacity.
- Control auto rotation speed.
- Enable X-Ray Waterline mode.
- Show a cross-section style view.
- Reset the camera.

# Technologies Used

- HTML
- CSS
- JavaScript
- Three.js
- WebGL

## Current Status

This is a prototype.

The fouling data is currently hard coded inside the HTML file. In the full system, this data should come from the AI biofouling detection model after processing ROV, diver, camera, or inspection images.

# Workflow

A full version of the project follow this workflow:

1. Collect hull inspection images or video.
2. Use an AI model to detect biofouling.
3. Estimate fouling thickness, density, and affected area.
4. Match the detection result to a hull zone.
5. Send the processed data to the 3D digital twin.
6. Display fouling severity on the vessel model.
7. Help users decide which zones need cleaning or further inspection.

# Future Improvements

Possible next steps:

- Connect the 3D viewer to real AI model output.
- Load fouling data from a JSON file or backend API.
- Add real vessel geometry from CAD or scan data.
- Add before-and-after cleaning comparison.
- Add inspection history for each hull zone.
- Export inspection reports.
- Show maintenance priority based on fouling severity.
- Improve mobile support.
- Fix text encoding issues in the current HTML file.

# Notes

The current demo is useful for explaining the concept and showing how AI results can become a 3D hull condition map.

It is not yet a final inspection system. The values shown in the demo should be treated as sample data until real model output and verified inspection measurements are connected.
