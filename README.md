# Gibbon Training - Balance Feedback App

A mobile-first web application that uses AI-powered pose detection to help users train their balance on a slackboard/slackline. The app tracks body position in real-time using the device's camera and provides visual feedback.

## Overview

This app is designed for balance training, specifically for slackboard/slackline practice. It uses MediaPipe Pose Detection to track the user's body and provides real-time feedback about arm positions and body visibility.

## Features

### 1. Balance Control Mode

The main feature of the app. Tracks your body position while balancing.

**User Flow:**
1. **Start Screen** - Shows instructions and two options:
   - **Start Button** - Begins a 5-second countdown, then starts tracking
   - **Check Camera Placement** - Preview camera to position yourself correctly

2. **Camera Check Mode** - Live camera feed (no pose detection) with a guide frame to help position the slackboard and ensure your whole body is visible. Press "Done" to return to start screen.

3. **Countdown** - 5-second animated countdown to get ready on the slackboard.

4. **Balance Measurement** - Active tracking mode that shows:
   - Arm position status: "L: UP/DOWN | R: UP/DOWN"
   - Pose skeleton overlay on camera feed
   - Real-time warnings if body parts move out of frame
   - Red "Stop" button to end the session

5. **Body Visibility Warnings** - Alerts when body parts are near the edge of the frame:
   - Hands and feet: warned at 12% from edge (earlier detection)
   - Other body parts: warned at 8% from edge
   - Shows which direction the body part is leaving (left/right/top/bottom)

6. **Session Dashboard** - After pressing Stop, see your training summary:
   - **Training Time** - Total session duration
   - **Left Arm Up Time** - How long your left arm was raised
   - **Right Arm Up Time** - How long your right arm was raised
   - **Arm Movement Chart** - Line graph showing when each arm was up/down over time
   - **Paused Time Info** - Shows time when tracking was paused due to body parts out of frame
   - Gray zones on chart indicate paused tracking periods
   - Options to "Start New Session" or "Back to Menu"

**Important:** Arm tracking is automatically paused when any body part moves out of frame. This ensures accurate statistics - only valid tracking time counts toward arm-up totals.

### 2. Other Modes (Coming Soon)

- **Squat Reps** - Count and track squat repetitions
- **Plank Hold** - Time your plank with form feedback
- **Push-up Reps** - Count and track push-up repetitions

## Technical Details

### Technologies Used
- **HTML5/CSS3/JavaScript** - Single-file web app (no build tools)
- **MediaPipe Pose** - AI pose detection (lite model for mobile performance)
- **PWA** - Installable as standalone app, works offline

### Key Files
| File | Purpose |
|------|---------|
| `index.html` | Main application (contains all HTML, CSS, and JavaScript) |
| `manifest.json` | PWA configuration for app installation |
| `sw.js` | Service Worker for offline caching |
| `icon.svg` | App icon |

### Pose Detection Settings
- Model complexity: 0 (lite, optimized for mobile)
- Detection confidence: 0.5
- Tracking confidence: 0.5
- Frame processing: Every 3rd frame (~10 FPS from 30 FPS video)

### Body Landmarks Tracked
- **Head**: Nose, ears
- **Arms**: Shoulders, elbows
- **Hands**: Wrist, pinky, index finger, thumb
- **Legs**: Hips, knees
- **Feet**: Ankles, heels, toes

## Installation

### As a Web App
Simply open `index.html` in a browser or host on any web server.

### As a Mobile App (PWA)
1. Open the app URL in mobile browser (Chrome/Safari)
2. Tap "Add to Home Screen"
3. The app will install and work offline

## Usage Tips

1. **Lighting** - Ensure good lighting for accurate pose detection
2. **Camera Position** - Place phone where your entire body is visible
3. **Distance** - Stand far enough that hands and feet don't leave the frame when balancing
4. **Clothing** - Wear clothes that contrast with the background

## Changelog

### 2024-XX-XX - Session Dashboard
- Added dashboard screen after stopping a session
- Display total training time, left arm up time, right arm up time
- Added line chart showing arm positions over time (left=teal, right=red)
- Track arm data at 100ms intervals during measurement
- Pause tracking when any body part is out of frame
- Show paused time and gray zones on chart for warning periods

### 2024-XX-XX - Body Visibility Warnings Improvement
- Increased edge margins for earlier detection (8% general, 12% for hands/feet)
- Added directional warnings (left/right/top/bottom)
- Separated hand and foot tracking for more precision

### 2024-XX-XX - Start/Stop Flow
- Added start screen with instructions
- Added "Check Camera Placement" mode
- Added 5-second countdown before measurement
- Added Stop button during measurement
- Added body visibility warnings

### 2024-XX-XX - Initial Release
- Balance Control mode with arm position tracking
- PWA support for offline use
- Mobile-optimized UI with landscape warning

## Repository

GitHub: https://github.com/mpurer/balance-technique-feedback

## Development Notes

### Balance State Machine
The balance mode uses these states:
- `start` - Initial screen with Start/Check Camera buttons
- `camera-check` - Camera preview without pose detection
- `countdown` - 5-second countdown animation
- `measuring` - Active pose detection and feedback
- `dashboard` - Session summary with statistics and chart

### Data Tracking
- Arm positions recorded every 100ms during measurement
- Data structure: `{time, leftUp, rightUp, hasWarning}`
- Warnings pause arm tracking but time continues
- Statistics calculated from recorded data points

### CSS Color Scheme
- Primary (yellow): `#E8FC66`
- Dark background: `#1a1a1a`
- Darker background: `#0d0d0d`
- Warning red: `#ff4444`
- Left arm (chart): `#4ECDC4` (teal)
- Right arm (chart): `#FF6B6B` (coral red)
