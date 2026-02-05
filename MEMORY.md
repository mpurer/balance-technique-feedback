# Claude Memory - Balance Feedback App

This file helps Claude (AI assistant) understand the project context when reopening.

## Project Info
- **Location**: `C:\Users\purer\Desktop\gibbon job\balance feedback`
- **Repo**: https://github.com/mpurer/balance-technique-feedback
- **Type**: Single-file web app (index.html) using MediaPipe Pose Detection
- **Platform**: PWA for mobile installation

## Current Status
- Balance Control mode: **Fully Implemented** (with dashboard)
- Squat Reps mode: Placeholder only
- Plank Hold mode: Placeholder only
- Push-up Reps mode: Placeholder only

## Balance Mode States
```
start → camera-check → countdown → measuring → dashboard
        (optional)                              ↓
                                         restart or back
```

## Important Reminders
- **Always update README.md and MEMORY.md when making changes**
- User wants documentation kept up to date for non-coders too

## Recent Work (Latest First)
1. **Session Dashboard** - Shows after pressing Stop:
   - Training time, left/right arm up times
   - Line chart with arm movement over time
   - Tracking pauses when body parts out of frame
   - Gray zones on chart show paused periods
2. Body visibility warnings (12% margin for hands/feet, 8% for others)
3. Start/stop flow with 5-second countdown
4. Camera check mode for positioning preview

## Key Technical Notes
- Video element `#video` is hidden (used by pose detection canvas)
- Camera check uses separate video element `#camera-check-video`
- Pose detection runs on every 3rd frame for performance
- Arm data recorded every 100ms: `{time, leftUp, rightUp, hasWarning}`
- Chart colors: Left arm = `#4ECDC4` (teal), Right arm = `#FF6B6B` (red)
- CSS primary color: `#E8FC66` (yellow)
