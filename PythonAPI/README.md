# Object Detection Evaluation Kit

This is now the Official Evaluation Kit for SenseMentor Object Detection Challenge.

This repository contains the evaluation scripts for the object detection challenges available at xxx.


## Overview 
- [Challenges](Challenges)
- [Requirements](Requirements)
- [Install](Install)
- [2D Detection Evaluation](2D Detection Evaluation)
- [Citation](Citation)
- [Acknowledgements](Acknowledgements)


## Challenges
TODO


## Requirements (TODO)
- [OpenCV](https://github.com/opencv/opencv)
- g++

## Install (TODO)
Please make sure you have installed all required dependencies. Execute:
```
git clone https://gitlab.senseauto.com/perceptionx/meta-add/sensementor
cd sensementor
make
```

## 2D Detection Evaluation

### Data Format
- Prepare your result json in directory following this structure:
```
|-- output_dir
|   |-- validation
|   |   |-- segment-xxx
|   |   |   |-- xxx.json
|   |   |   |-- ...
|   |   |-- segment-xxx
|   |   |   |-- xxx.json
|   |   |   |-- ...
|   |   |-- ...
```
- Each json should include result following this structure:
```
{
    "results": [
        {
            "width": 514.1142599999998,     <int> -- bbox width
            "height": 342.32178,            <int> -- bbox width
            "x": 1405.28775,                <int> -- top-left pixel coordination of u
            "y": 745.2762,                  <int> -- top-left pixel coordination of v
            "id": "4",                      <int> -- cipo level
            "type": 1                       <int> -- object category
        },
    ],
    "raw_file_path":                        <str> -- image path, for example:
                                    "training/segment-1146261869236413282_1680_000_1700_000_with_camera_labels/155840113544766700.jpg"
```


### Evaluation
To run the evaluation for your method please run the script:
```
./evaluate -a $dataset_dir  -d $output_dir -i $image_dir -l $list -w $w_lane -t $iou -c $im_w -r $im_h -f $frame -o $output_file
```

The basic arguments are described below.

`dataset_dir`: Data path of SenseMentor dataset 

`image_dir`: Image path of SenseMentor dataset

`list`: Image list which will be evaluated (you can find an example in SenseMentor/demo/validation.txt)

`output_dir`: Detection results path

`w_lane`: Lane width, 30 in original [SCNN](https://github.com/XingangPan/SCNN) paper

`iou`: IOU threshold used for evaluation, 0.3/0.5 in original [SCNN](https://github.com/XingangPan/SCNN) paper

`im_w`: Width of the original image

`im_h`: Height of the original image

`frame`: Frame, should be 1

`output_file`: Evaluation outputs file path

### Metric formula
We adopt the evaluation metric in [SCNN](https://github.com/XingangPan/SCNN). TODO
