# VLAdoggo

## Current Plan:

1. A microphone captures the user’s voice command.
2. The audio is transcribed to text using Whisper (locally on Jetson or via API).
3. The transcribed command is sent to an LLM (via a simple Flask API) to generate a structured action plan.
4. Jetson runs an object detection model (e.g., YOLO) on the live camera feed to identify target objects.
5. The system computes relative positions (bearing, distance) of detected objects.
6. The `structured command and visual data are combined` to select the target and plan the task.
7. ROS 2 Navigation (Nav2) uses the selected target to generate a motion plan.
8. Unitree Go2 executes movement via its SDK or ROS interface.
9. As the scene and camera feed changes, any new information `triggers repeat from point 6.`