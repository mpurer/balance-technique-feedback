# Claude Memory - Balance Feedback App

This file helps Claude (AI assistant) understand the project context when reopening.

## Project Info
- **Location**: `C:\Users\purer\Desktop\gibbon job\balance feedback`
- **Repo**: https://github.com/mpurer/balance-technique-feedback
- **Type**: Single-file web app (index.html) using MediaPipe Pose Detection
- **Platform**: PWA for mobile installation

## Current Status
- Balance Control mode: **Implemented**
- Squat Reps mode: Placeholder only
- Plank Hold mode: Placeholder only
- Push-up Reps mode: Placeholder only

## Balance Mode States
```
start → camera-check → countdown → measuring
        (optional)
```

## Important Reminders
- **Always update README.md when making changes**
- User wants documentation kept up to date for non-coders too

## Recent Work
- Added start/stop flow with countdown
- Added camera check mode for positioning preview
- Added body visibility warnings (hands/feet at 12% margin, others at 8%)
- Warnings show direction (left/right/top/bottom)

## Key Technical Notes
- Video element `#video` is hidden (used by pose detection canvas)
- Camera check uses separate video element `#camera-check-video`
- Pose detection runs on every 3rd frame for performance
- CSS primary color: `#E8FC66` (yellow)
