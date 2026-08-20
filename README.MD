# Implementation of **DEGAST3D: Learning Deformable 3D Graph Similarity to Track Plant Cells in Unregistered Time Lapse Images (https://ieeexplore.ieee.org/document/10820545 Published in IEEE Transactions on Computational Biology and Bioinformatics)**

# **3D Plant Cell Segmentation, Tracking, and Cell Division Detection**

## **Overview**
This project performs **3D segmentation, registration, tracking, and cell division detection** for plant cell images using deep learning-based approaches. It leverages **Cellpose** for segmentation and implements a **3D Graph Matching** approach for tracking plant cells and detecting cell division events.

## **Features**
✅ **Automated 3D segmentation** using **Cellpose**
✅ **Automated 3D registration**  
✅ **Supports multiple plant datasets** for microscopic image analysis  
✅ **Performs plant cell tracking** using **3D graph-based matching**  
✅ **Detects cell division events**  

---

## **Installation**
### **1. Install Dependencies**
Create the required Conda environment using:
```bash
conda env create -f environment.yml
```

---

## **Project Structure**
```
project_root/
├── segmentation.py         # 3D segmentation script using Cellpose
├── Registration.py         # Registration script for aligning time-lapse images
├── Inference_Tracking_Celldiv.py  # Combined script for registration, tracking & division detection
├── data_process.py         # Functions for data preprocessing
├── data/                   # Dataset directory (organized by plant)
│   ├── plant_1/
│   │   ├── microscopic_images/     # Raw images
│   │   ├── cellpose/               # Segmentation results
│   │   │   ├── seg/                # Segmented masks
│   │   |	├── stack_info/             # Processed stack information
│   │   |	├── Registration_info/      # Registration details
│   ├── plant_2/
│   ├── plant_4/
│   ├── plant_13/
│   ├── plant_15/
│   ├── plant_18/
│   ├── test_plant/
├── results/                # Output directory for segmentation, tracking, and cell division data
└── README.md               # Project documentation
```

---

## **Usage**
### **1. Define Plant Names**
Ensure the following plant names are set in `segmentation.py` and `Inference_Tracking_Celldiv.py`:
```python
plant_names = ['plant_1', 'plant_2', 'plant_4', 'plant_13', 'plant_15', 'plant_18', 'test_plant']
```

### **2. Prepare the Dataset**
Place your microscopic image dataset inside the `data` directory, following the structure:
```
data/
├── plant_1/
│   ├── microscopic_images/
│   ├── cellpose/
│   │   ├── seg/
│   |	├── stack_info/
│   |	├── Registration_info/
├── plant_2/
├── ...
```

### **3. Run Segmentation**
Execute the segmentation script by specifying the **dataset directory and plant index**: This script also includes data processing using `STACK_INF0_3D` and `STACK_INF0_Registration`. 
```bash
python segmentation.py --main_dir "data" --plant_idx 6 --segmentation "cellpose"
```
📌 **Output:** Segmented masks will be saved in the `seg/` directory inside the respective plant folder.
The processed data will also be saved in `stack_info` and  `Registration_info` sub-folder.


### **4. Run Registration, Tracking and Cell Division Detection for every pair of timepoint**
Perform **Registration , Tracking and Cell division detection** in one step:
```bash
python Inference_Tracking_Celldiv.py --main_dir "data" --plant_idx 6 --segmentation "cellpose"
```
📌 **Output:** Tracking and division results will be stored inside `results/{segmentation}_{plant_name}/`.

---

## **Customization**
- Change `--plant_idx` to select a different plant dataset.
- The framework supports **any segmentation algorithm**.

---

## **Acknowledgments**
This project utilizes:
- **[Cellpose](https://github.com/MouseLand/cellpose)** for deep learning-based cell segmentation.
- **3D Graph** was constructed based on this reposititory **[Deep Graphical Feature Learning for the Feature Matching Problem](https://github.com/zzhang1987/Deep-Graphical-Feature-Learning)**, ICCV2019
- **This work was supported in part by the U.S. National Science Foundationunder grants OAC-2411453, OAC-1664172, DMS-1762063, DMS-2029814, and IOS-2055690.

---

## **License**
Academic Software License: © 2025 UCR (“Institution”). Academic or nonprofit researchers
are permitted to use this Software (as defined below) subject to Paragraphs 1-4:
1. Institution hereby grants to you free of charge, so long as you are an academic or
nonprofit researcher, a nonexclusive license under Institution’s copyright ownership
interest in this software and any derivative works made by you thereof (collectively, the
“Software”) to use, copy, and make derivative works of the Software solely for
educational or academic research purposes, and to distribute such Software free of charge
to other academic or nonprofit researchers for their educational or academic research
purposes, in all cases subject to the terms of this Academic Software License. Except as
granted herein, all rights are reserved by Institution, including the right to pursue patent
protection of the Software.
2. Any distribution of copies of this Software -- including any derivative works made by
you thereof -- must include a copy (including the copyright notice above), and be made
subject to the terms, of this Academic Software License; failure by you to adhere to the
requirements in Paragraphs 1 and 2 will result in immediate termination of the license
granted to you pursuant to this Academic Software License effective as of the date you
first used the Software.
3. IN NO EVENT WILL INSTITUTION BE LIABLE TO ANY ENTITY OR PERSON
FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, INCLUDING LOST PROFITS, ARISING OUT OF THE USE OF THIS
SOFTWARE, EVEN IF INSTITUTION HAS BEEN ADVISED OF THE POSSIBILITY
OF SUCH DAMAGE. INSTITUTION SPECIFICALLY DISCLAIMS ANY AND ALL
WARRANTIES, EXPRESS AND IMPLIED, INCLUDING, BUT NOT LIMITED TO,
ANY IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
PARTICULAR PURPOSE. THE SOFTWARE IS PROVIDED “AS IS.” INSTITUTION
HAS NO OBLIGATION TO PROVIDE MAINTENANCE, SUPPORT, UPDATES,
ENHANCEMENTS, OR MODIFICATIONS OF THIS SOFTWARE.
4. Any academic or scholarly publication arising from the use of this Software or any
derivative works thereof will include the following acknowledgment:  The Software
used in this research was created by Amit Roy-Chowdhury and members of the
Vision and Learning Group at UCR. © 2025 UCR.
Commercial entities: please contact amitrc@ucr.edu or otc@ucr.edu for licensing
opportunities.

