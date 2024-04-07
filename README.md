🚨 **Emergency-Vehicle-Detection** 🚨

**before detecting**
<video src = "https://github.com/sanket96s/Emergency-Vehicle-Detection/assets/109816069/f96a5785-2b02-4091-99fd-cb10e5fd227d" width=180 />

**after detecting**<br>
<video src = "https://github.com/sanket96s/Emergency-Vehicle-Detection/assets/109816069/1ae2b669-3dba-4204-8f0d-5ee44b141752" width=180 />

### Let's train a custom model using yolov8m object detection model library to detect emergency vehicles from the Given Input Image, Video, or Webcam.

**Prerequisites:**
- Python
- Anaconda
- Anaconda Command Prompt

1. **Setting up Environment:**
   - Open Anaconda terminal and navigate to the directory of the folder "Emergency Vehicle Detection" if don't have folder create it.
   - Create a virtual Python environment by running:
     
     ```
     conda create -n trainModel python=3.9
     ```
     
   - Activate the environment:
     
     ```
     conda activate trainModel
     ```

2. **Preparing the Data:**
   - Create separate folders named "images" and "labels" inside the "Emergency Vehicle Detection" folder.
   - Download or clone images into the "images" folder from the "images" folder of this repo.
   - Install LabelImg:
     
     ```
     pip install labelImg
     ```
     
   - Run LabelImg:
     
     ```
     labelImg
     ```
     
     - in navbar click file option and then click "Open dir" option and select the "images" folder.
     - in same navigation inside file click "change save dir" then select the "labels" folder.
     - in left vertical navigation side check that above "create react box" the "YOLO" is selected if not click pascalVOC</> it will select "YOLO".
     - click "create react box" and Create bounding boxes around emergency vehicles and label them accordingly.

3. **Splitting Data for Training and Validation:**
   - Create folders named "train" and "val" inside the "Emergency Vehicle Detection" folder.
   - Inside the "val" folder, create "images" and "labels" folders.
   - Move some images and labels from the "images" and "labels" folders to the "val/images" and "val/labels" folders, respectively.

4. **Creating Configuration Files:**
   - Create a "classes.txt" file in the "Emergency Vehicle Detection" folder.
   - Move the "images" and "labels" folders into the "train" folder.
   - Create a "data_detection.yaml" file in the "Emergency Vehicle Detection" folder.
   - copy the code of "data_detection.yaml" and "classes.txt" from this repo.
   - inside "data_detection.yaml" path should be updated according to the your folders(for train and val).

5. **Installing Dependencies:**
   - Install Ultralytics:
     
     ```
     pip install ultralytics
     ```

6. **Training the Model:**
   - Visit the PyTorch official website and select the appropriate settings for your system for downloading.
   - Copy the installation command and add `--upgrade` after the `install` keyword.
   - command look like
     
     ```
     pip3 install --upgrade torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
     ```
     
   - Run the command in the active virtual environment.
   - Train the model:
     ```
     yolo task=detect mode=train epochs=100 data=data_detection.yaml model=yolov8m.pt imgsz=640 batch=8
     ```
   - Note: Training may take several hours.

7. **Tesing Model**
   - go to dir "Emergency Vehicle Detection\runs\detect\train\weights"
   - copy best.pt and last.pt and paste at "Emergency Vehicle Detection"
   - rename best.pt to trainModel.pt
   - download the sampleA1.mp4 from this repo and paste at "Emergency Vehicle Detection"
   - run the below command in virtual environment
     
     ```
     yolo task=detect mode=predict model=trainModel.pt show=True conf=0.5 source=sampleA2.mp4
     ```
   NOTE : replace source=sampleA2.mp4 by your video.
   - You can try with images also
   - here the output comes wrong sometime because we trained this model with few images if we do with more the accurancy should be more

8. **Counting vehicle**
   - for counting vehicle copy code from "count.py" replace video link by your and run
   - dont use sampleA2.mp4 as it has different frame insteat use sampleA1.m4

<img src="https://github.com/ADITYAP2003/Emergency-Vehicle-Detection-and-Traffic-Management/assets/125755687/e73349a9-cc36-45d7-994b-d4a91c04efde">
