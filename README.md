# SKGE-SWIN: End-To-End Autonomous Vehicle Waypoint Prediction and Navigation Using Skip Stage Swin Transformer 

## Notes:
1. Some files are copied and modified from [[TransFuser, CVPR 2021]](https://github.com/autonomousvision/transfuser) repository. Please go to their repository for more details.
2. I assume you are familiar with Linux, python3, NVIDIA CUDA Toolkit, PyTorch GPU, and other necessary packages. Hence, I don't have to explain much detail.
3. Install Unreal Engine 4 and CARLA:
    - For UE4, follow: https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/Linux/BeginnerLinuxDeveloper/SettingUpAnUnrealWorkflow/
    - For CARLA, go to https://github.com/carla-simulator/carla/releases/tag/0.9.10.1 and download prebuilt CARLA + additional maps. Then, extract them to a directory (e.g., ~/OSKAR/CARLA/CARLA_0.9.10.1)

## Steps:
1. Download the dataset and extract to subfolder data. Or generate the data by yourself.
2. To train-val-test each model, go to their folder and read the instruction written in the README.md file
    - [skgeswin](https://github.com/fachrinnk4869/skge-swin/tree/main/skgeswin) (proposed model)
    - [skgeswin_16](https://github.com/fachrinnk4869/skge-swin/tree/main/skgeswin_16) (proposed model float 16)
    - [X13](https://github.com/fachrinnk4869/skge-swin/tree/main/x13) 
    - [S13](https://github.com/fachrinnk4869/skge-swin/tree/main/s13) (proposed model without SDC mapping)
    - [CILRS](https://github.com/fachrinnk4869/skge-swin/tree/main/cilrs)
    - [AIM](https://github.com/fachrinnk4869/skge-swin/tree/main/aim)
    - [LF](https://github.com/fachrinnk4869/skge-swin/tree/main/late_fusion)
    - [GF](https://github.com/fachrinnk4869/skge-swin/tree/main/geometric_fusion)
    - [TF](https://github.com/fachrinnk4869/skge-swin/tree/main/transfuser)
3. To use our trained skgeswin models, download [here](https://huggingface.co/fachrinnk4869/skgeswin/blob/main/best_model.pth)
3. or use skgeswin_16 models, download [here](https://huggingface.co/fachrinnk4869/skgeswin_16/blob/main/best_model.pth)

## Generate Data and Automated Driving Evaluation:
1. Run CARLA server:
    - CUDA_VISIBLE_DEVICES=0 ./CARLA/CarlaUE4.sh -opengl --world-port=2000
2. To generate data / collect data, Run expert (results are saved in subfolder 'data'):
    - CUDA_VISIBLE_DEVICES=0 ./leaderboard/scripts/run_expert.sh
3. For automated driving, Run agents (results are saved in subfolder 'data'):
    - CUDA_VISIBLE_DEVICES=0 ./leaderboard/scripts/run_evaluation.sh

## To do list:
1. Add download link for the dataset (The dataset is very large. I recommend you to generate the dataset by yourself :D)