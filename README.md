🎥➡️⚡ v2e: Video to Events Converter
This project converts conventional stroboscopic video frames (low frame rate) into realistic synthetic DVS (Dynamic Vision Sensor) event streams with much higher effective temporal resolution using PyTorch and OpenCV. The conversion simulates neuromorphic camera behavior including photoreceptor dynamics and noise modeling.

✨ Features
Converts standard video to synthetic DVS event stream

Realistic photoreceptor intensity-dependent bandwidth simulation

Gaussian pixel-to-pixel event threshold variation

Noise modeling with 'leak' events

Adjustable timing precision and DVS exposure settings

🛠️ Installation
Create and activate a conda environment (ensure PyTorch is installed):

bash
Copy
Edit
conda create -n v2e python=3.8
conda activate v2e
conda install pytorch torchvision -c pytorch
Clone the repository and install dependencies:

bash
Copy
Edit
git clone https://github.com/SensorsINI/v2e
cd v2e
python -m pip install -e .
▶️ Usage
Run the conversion script using your video file:

bash
Copy
Edit
python v2e.py \
  -i input/tennis.mov \
  --overwrite \
  --timestamp_resolution=0.003 \
  --auto_timestamp_resolution=False \
  --dvs_exposure duration 0.005 \
  --output_folder=output/tennis \
  --pos_thres=0.15 \
  --neg_thres=0.15 \
  --sigma_thres=0.03 \
  --dvs_aedat2 tennis.aedat \
  --output_width=346 \
  --output_height=260 \
  --stop_time=3 \
  --cutoff_hz=15
🔧 Key Parameters
Parameter	Description
--timestamp_resolution	Effective event time resolution in seconds
--dvs_exposure	Exposure duration per frame (affects output density)
--pos_thres / --neg_thres	Positive/Negative threshold for triggering events
--sigma_thres	Std. deviation for per-pixel threshold noise
--cutoff_hz	Photoreceptor lowpass filter cutoff frequency
--output_width/height	Resolution of output DVS stream
--stop_time	Limit processing to the first N seconds of the video

📂 Output
AER file: DVS event stream in .aedat2 format

Log files: Metadata and statistics

Visualizations: (optional) Preview of the DVS event stream