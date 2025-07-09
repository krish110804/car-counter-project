# Vehicle Counter using YOLOv8 and SORT Tracking

A real-time vehicle counting system that uses YOLOv8 for object detection and SORT algorithm for multi-object tracking. The system can count cars, trucks, buses, and motorbikes crossing a predefined line in a video feed.

## Features

- **Real-time Detection**: Uses YOLOv8 for fast and accurate vehicle detection
- **Multi-Object Tracking**: Implements SORT algorithm to track vehicles across frames
- **Vehicle Counting**: Counts vehicles crossing a specified line with unique ID tracking
- **Multiple Vehicle Types**: Detects cars, trucks, buses, and motorbikes
- **Masked Region Processing**: Focuses detection on specific areas using mask images
- **Visual Feedback**: Real-time display with bounding boxes, tracking IDs, and count overlay

## Demo
![Screenshot 2025-07-09 230806](https://github.com/user-attachments/assets/9e61bbba-9a11-41ee-86e5-3f129ec6f498)

*Real-time vehicle counting with tracking visualization*

## Requirements

### Python Dependencies

```bash
pip install ultralytics opencv-python cvzone numpy
```

### Additional Files Required

- `sort.py` - SORT tracking algorithm implementation
- `mask.png` - Binary mask image to define counting region
- `graphics.png` - Overlay graphics for UI enhancement
- `cars.mp4` - Input video file for processing

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/vehicle-counter.git
   cd vehicle-counter
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download SORT implementation**
   ```bash
   # Download sort.py from the official SORT repository
   wget https://raw.githubusercontent.com/abewley/sort/master/sort.py
   ```

4. **Prepare your files**
   - Place your video file as `cars.mp4`
   - Create a binary mask image `mask.png` to define the counting region
   - Add any overlay graphics as `graphics.png`

## Project Structure

```
vehicle-counter/
├── carcounter.py          # Main application file
├── sort.py                # SORT tracking algorithm
├── mask.png               # Binary mask for region of interest
├── graphics.png           # UI overlay graphics
├── cars.mp4               # Input video file
├── requirements.txt       # Python dependencies
└── README.md             # This file
```

## Usage

### Basic Usage

```bash
python carcounter.py
```

### Key Controls

- **'q'**: Quit the application
- **Video Window**: Shows real-time detection and counting

### Configuration

You can modify the following parameters in `carcounter.py`:

```python
# Video resolution
cap.set(3, 950)  # Width
cap.set(4, 480)  # Height

# Counting line coordinates [x1, y1, x2, y2]
limits = [400, 297, 673, 297]

# Confidence threshold for detections
if conf > 0.3:  # Adjust confidence threshold

# Tracker parameters
tracker = Sort(max_age=20, min_hits=3, iou_threshold=0.3)
```

## How It Works

1. **Video Processing**: Reads video frames from the input file
2. **Mask Application**: Applies binary mask to focus on specific regions
3. **Object Detection**: Uses YOLOv8 to detect vehicles in each frame
4. **Tracking**: SORT algorithm tracks detected objects across frames
5. **Counting Logic**: Counts unique vehicles crossing the predefined line
6. **Visualization**: Displays bounding boxes, IDs, and current count

## Supported Vehicle Types

- Cars
- Trucks
- Buses
- Motorbikes

## Creating a Mask Image

To create your own mask image:

1. Use any image editing software (GIMP, Photoshop, etc.)
2. Create a binary image where:
   - **White areas** (255): Regions to process
   - **Black areas** (0): Regions to ignore
3. Save as `mask.png` in the project directory

## Troubleshooting

### Common Issues

1. **"mask.png not found"**
   - Ensure `mask.png` is in the same directory as `carcounter.py`
   - Check file permissions

2. **"graphics.png not found"**
   - Ensure `graphics.png` is in the project directory
   - You can comment out the overlay line if not needed

3. **Low detection accuracy**
   - Adjust confidence threshold
   - Improve lighting conditions in video
   - Use higher resolution video

4. **Tracking issues**
   - Modify SORT parameters (`max_age`, `min_hits`, `iou_threshold`)
   - Ensure smooth video without abrupt cuts

## Performance Optimization

- Use GPU acceleration with CUDA if available
- Reduce video resolution for faster processing
- Adjust confidence threshold based on accuracy requirements
- Use appropriate mask to reduce processing area

## Technical Details

### Dependencies

- **ultralytics**: YOLOv8 implementation
- **opencv-python**: Computer vision operations
- **cvzone**: Computer vision utilities
- **numpy**: Numerical operations
- **sort**: Multi-object tracking algorithm

### Model Information

- **Model**: YOLOv8n (nano version for speed)
- **Classes**: 80 COCO dataset classes
- **Input**: RGB video frames
- **Output**: Bounding boxes with confidence scores

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Ultralytics](https://github.com/ultralytics/ultralytics) for YOLOv8
- [SORT](https://github.com/abewley/sort) for multi-object tracking
- [CVZone](https://github.com/cvzone/cvzone) for computer vision utilities

## Future Enhancements

- [ ] Real-time webcam support
- [ ] Speed estimation
- [ ] Vehicle classification accuracy improvements
- [ ] Export counting data to CSV
- [ ] Web-based interface
- [ ] Multiple counting lines support
- [ ] Traffic density analysis

## Contact

email:- krish17aug04@gmail.com

---

⭐ If you found this project helpful, please give it a star!
