# YOLOv8 Live Detection

A simple real-time object detection system using YOLOv8 with angle calculation and optional Arduino serial communication.

## Features

- Real-time object detection using YOLOv8
- Angle calculation from frame center to detected objects
- Support for webcam, video files, and images
- Visual annotations with bounding boxes and angle display
- Optional Arduino serial communication (commented out)

## Requirements

```bash
pip install ultralytics
pip install opencv-python
pip install supervision
pip install numpy
```

## Usage

### Basic Usage

```bash
# Run with default webcam
python main.py

# Run with custom resolution
python main.py --webcam-resolution 1920 1080

# Run with video file
python main.py --input path/to/video.mp4

# Run with image
python main.py --input path/to/image.jpg
```

### Command Line Arguments

| Argument | Description | Default | Example |
|----------|-------------|---------|---------|
| `--webcam-resolution` | Camera resolution (width height) | [1280, 720] | `--webcam-resolution 640 480` |
| `--input` | Input source (webcam/video/image) | "webcam" | `--input video.mp4` |

## Model Setup

1. Place your trained YOLOv8 model in the desired location
2. Update the model path in the code:
```python
model = YOLO("/path/to/your/model.pt")
```

## How It Works

1. **Object Detection**: Uses YOLOv8 to detect objects in real-time
2. **Angle Calculation**: Calculates angle from frame center to each detected object
3. **Visual Feedback**: Draws bounding boxes, midpoints, and angle lines
4. **Serial Communication**: (Optional) Sends angle data to Arduino

## Controls

- **ESC**: Exit the application
- **Ctrl+C**: Interrupt and exit safely

## Code Structure

- `parse_arguments()`: Command line argument parsing
- `calculate_angle()`: Computes angle from frame center to object
- `draw_annotations()`: Draws visual annotations on frame
- `main()`: Main detection loop

## Arduino Integration

The code includes commented Arduino serial communication:

```python
# Uncomment these lines to enable Arduino communication
# from arduinoSerialCom import ArduinoSerial
# arduino = ArduinoSerial(115200, '/dev/ttyACM0')
```

## Example Output

The system will display:
- Live video feed with detection boxes
- Green lines from frame center to detected objects
- Angle values displayed near each detection
- Object class names and confidence scores

---

**Note**: This is a basic implementation for educational/development purposes. Update model paths and Arduino settings according to your setup.
