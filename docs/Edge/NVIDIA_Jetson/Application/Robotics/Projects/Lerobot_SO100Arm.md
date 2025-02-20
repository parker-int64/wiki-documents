---
description: This wiki provides the assembly and debugging tutorial for the SO ARM100 and realizes data collection and training within the Lerobot framework. 
title: How to use the SO100Arm robotic arm in Lerobot
keywords:
- Lerobot
- Huggingface
- Arm
- Robotics
image: https://files.seeedstudio.com/wiki/wiki-platform/S-tempor.png
slug: /lerobot_so100m
last_update:
  date: 12/24/2024
  author: ZhuYaoHui
---

## How to use the SO-ARM100 robotic arm in Lerobot

The [SO-100ARM](https://github.com/TheRobotStudio/SO-ARM100) is a fully open-source robotic arm project launched by [TheRobotStudio](https://www.therobotstudio.com/). It includes the follower arm and the leader robotic arm, and also provides detailed 3D printing files and operation guides. [LeRobot](https://github.com/huggingface/lerobot/tree/main) is committed to providing models, datasets and tools for real-world robotics in PyTorch. Its aim is to reduce the entry barrier of robotics, enabling everyone to contribute and benefit from sharing datasets and pretrained models. LeRobot integrates cutting-edge methodologies validated for real-world application, centering on imitation learning and reinforcement learning. It has furnished a suite of pre-trained models, datasets featuring human-gathered demonstrations, and simulation environments, enabling users to commence without the necessity of robot assembly. In the forthcoming weeks, the intention is to augment support for real-world robotics on the most cost-effective and competent robots presently accessible. 

<iframe width="960" height="640" src="https://www.youtube.com/embed/sD34HnAkGNc?si=hqKd_sH5Oc9sdcwd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


### Projects Introduction
The SO-ARM100 and reComputer Jetson AI intelligent robot kit seamlessly combine high-precision robotic arm control with a powerful AI computing platform, providing a comprehensive robot development solution. This kit is based on the Jetson Orin or AGX Orin platform, combined with the SO-ARM100 robotic arm and the LeRobot AI framework, offering users an intelligent robot system applicable to multiple scenarios such as education, research, and industrial automation.
This wiki provides the assembly and debugging tutorial for the SO ARM100 and realizes data collection and training within the Lerobot framework. 

  <div align="center">
      <img width={800} 
      src="https://files.seeedstudio.com/wiki/robotics/projects/lerobot/Arm_kit.png" />
  </div>

<div class="get_one_now_container" style={{textAlign: 'center'}}>
<a class="get_one_now_item" href="https://www.seeedstudio.com/reComputer-J4012-p-5586.html">
            <strong><span><font color={'FFFFFF'} size={"4"}> Get One Now 🖱️</font></span></strong>
</a></div>

### Main Features
1. **High-Precision Robotic Arm**: The SO-ARM100 robotic arm employs high-precision servo motors and advanced motion control algorithms, and is suitable for a variety of tasks such as grasping, assembly, and inspection.
2. **reComputer Jetson Platform**: It uses the SeeedStudio reComputer Jetson Orin or AGX Orin Dev Kit as the AI computing platform, which supports deep learning, computer vision, and data processing tasks, providing powerful computing capabilities.
3. **AI-Driven**: It integrates the LeRobot AI framework of Hugging Face, supports natural language processing (NLP) and computer vision, enabling the robot to intelligently understand instructions and perceive the environment.
4. **Open Source and Flexible Expansion**: It is an open-source platform that is easy to customize and expand, suitable for developers and researchers to conduct secondary development, and supports the integration of multiple sensors and tools.
5. **Multi-Scene Application**: It is applicable to fields such as education, scientific research, automated production, and robotics, helping users achieve efficient and precise robot operations in various complex tasks. 

### Specification
| Specification | Arm Kit | Arm Kit Pro |
|--|--|--|
| Type | Arm Kit | Arm Kit Pro |
| Degree of freedom | 6 | 6 |
| Max Torque | 19.5kg.cm 7.4V | 30kg.cm 12V |
| Servo | STS3215 Bus Servo | STS3215 Bus Servo |
| Power Supply | 5.5mm*2.1mm DC 5V4A | 5.5mm*2.1mm DC 12V1A |
| Angle sensor | 12-bit magnetic encoder | 12-bit magnetic encoder |
| Recommended Operating Temperature Range | 0℃～40℃ | 0℃～40℃ |
| Communication Method | UART | UART |
| Control Method | PC | PC |

### Bill of Materials(BOM)

| Part | Amount | Included|
|--|--|--|
| STS3215 Servo1 | 12 | ✅ |
| Motor Control Board | 2 | ✅ |
| USB-C Cable 2 pcs | 1 | ✅ |
| Power Supply2 | 2 | ✅ |
| Table Clamp| 1 | ❌ |
| 3D printed parts of the arm | 1 | ❌ |

:::caution
The 3D printed parts and table clamps are not included in the product. However, the SO-100ARM provides detailed [3D printing STL files](https://github.com/TheRobotStudio/SO-ARM100/tree/main/stl_files_for_3dprinting) and printing parameters. Besides, we also offer the [3D printed parts of the Table Clamp](https://makerworld.com/zh/models/908660).
:::

### 3D Printing Guide
A variety of 3D printers are acceptable to print the parts necessary of the follower and leader arm. Follow the steps below to ensure a good print. 
1. Choose a printer: The STL files provided ready to print on many FDM printers. Below are the tested and suggested settings though others may work.
    - Material: PLA
    - Nozzle Diameter and Precision: 0.4mm nozzle diameter at 0.2mm layer height or 0.6mm nozzle at 0.4mm layer height.
    - Infill Density: 13%

2. Acquisition of 3D printing files: All the parts for the leader or follower are contained in a single file, correctly orientated for z upwards to minimize supports.

    For printer bed sizes of 220mmx220mm (such as the Ender), print:
    - [Print_Follower_SO_ARM100_08_Ender.STL](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Follower/Print_Follower_SO_ARM100_08k_Ender.STL)
    - [Print_Leader_SO_ARM100_08_Ender.STL](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Leader/Print_Leader_SO_ARM100_08k_Ender.STL)

    For printer bed sizes of 205mm x 250mm (such as the Prusa/Up), print:
    - [Print_Follower_SO_ARM100_08_UP_Prusa.STL](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Follower/Print_Follower_SO_ARM100_08k_UP_Prusa.STL)
    - [Print_Leader_SO_ARM100_08_UP_Prusa.STL](https://github.com/TheRobotStudio/SO-ARM100/blob/main/stl_files_for_3dprinting/Leader/Print_Leader_SO_ARM100_08k_UP_Prusa.STL)

For the convenience of downloading, we have already packaged all the files on the [Makerworld platform](https://makerworld.com/zh/models/908660), including the Table Clamps.


### Install LeRobot

On your reComputer Nvidia Jetson:
1. Install Miniconda:
```bash
mkdir -p ~/miniconda3
cd ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh
chmod +x Miniconda3-latest-Linux-aarch64.sh
./Miniconda3-latest-Linux-aarch64.sh
```
2. Restart shell or `source ~/.bashrc`

3. Create and activate a fresh conda environment for lerobot
```bash 
conda create -y -n lerobot python=3.10 && conda activate lerobot
```

4. Clone Lerobot:
```bash
git clone https://github.com/huggingface/lerobot.git ~/lerobot
```

5. Install LeRobot with dependencies for the feetech motors:

```bash
cd ~/lerobot && pip install -e ".[feetech]"
```
For Linux only (not Mac), install extra dependencies for recording datasets:
```bash
conda install -y -c conda-forge ffmpeg
pip uninstall -y opencv-python
conda install -y -c conda-forge "opencv>=4.10.0"
```

### Configure the motors

Follow steps 1 of the [assembly video](https://www.youtube.com/watch?v=FioA2oeFZ5I) which illustrates the use of our scripts below.

<iframe width="960" height="640" src="https://www.youtube.com/embed/FioA2oeFZ5I?si=GjudmAovwF_X5m2f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


**Find USB ports associated to your arms**
To find the correct ports for each arm, run the utility script twice:
```bash
python lerobot/scripts/find_motors_bus_port.py
```

Example output when identifying the leader arm's port (e.g., `/dev/tty.usbmodem575E0031751` on Mac, or possibly `/dev/ttyACM0` on Linux):

Example output when identifying the follower arm's port (e.g., `/dev/tty.usbmodem575E0032081`, or possibly `/dev/ttyACM1` on Linux):

Troubleshooting: On Linux, you might need to give access to the USB ports by running:
```bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

**Configure your motors**
Plug your first motor and run this script to set its ID to 1. It will also set its present position to 2048, so expect your motor to rotate:
```bash
python lerobot/scripts/configure_motor.py \
  --port /dev/ttyACM0 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 1
```

Note: These motors are currently limitated. They can take values between 0 and 4096 only, which corresponds to a full turn. They can't turn more than that. 2048 is at the middle of this range, so we can take -2048 steps (180 degrees anticlockwise) and reach the maximum range, or take +2048 steps (180 degrees clockwise) and reach the maximum range. The configuration step also sets the homing offset to 0, so that if you misassembled the arm, you can always update the homing offset to account for a shift up to ± 2048 steps (± 180 degrees).

Then unplug your motor and plug the second motor and set its ID to 2.

```bash
python lerobot/scripts/configure_motor.py \
  --port /dev/ttyACM0 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 2
```

Redo the process for all your motors until ID 6. Do the same for the 6 motors of the leader arm.

### Assembly
Detailed video instructions are on the [HuggingFace Youtube](https://www.youtube.com/watch?v=FioA2oeFZ5I)

<iframe width="960" height="640" src="https://www.youtube.com/embed/FioA2oeFZ5I?si=GjudmAovwF_X5m2f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


### Calibrate

Next, you'll need to calibrate your SO-100 robot to ensure that the leader and follower arms have the same position values when they are in the same physical position. This calibration is essential because it allows a neural network trained on one SO-100 robot to work on another.

:::info
The calibration of the robotic arm should be carried out strictly in accordance with the ["Calibrate"](https://github.com/huggingface/lerobot/blob/main/examples/10_use_so100.md#calibrate) steps in the official tutorial of Lerobot.
:::


**Manual calibration of follower arm**

Contrarily to step 6 of the [assembly video](https://www.youtube.com/watch?v=FioA2oeFZ5I) which illustrates the auto calibration, we will actually do manual calibration of follower for now.

<iframe width="960" height="640" src="https://www.youtube.com/embed/FioA2oeFZ5I?si=GjudmAovwF_X5m2f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


You will need to move the follower arm to these positions sequentially:

Make sure both arms are connected and run this script to launch manual calibration:
```bash
python lerobot/scripts/control_robot.py calibrate \
    --robot-path lerobot/configs/robot/so100.yaml \
    --robot-overrides '~cameras' --arms main_follower
```

**Manual calibration of leader arm**
Follow step 6 of the [assembly video](https://www.youtube.com/watch?v=FioA2oeFZ5I) which illustrates the manual calibration. You will need to move the leader arm to these positions sequentially:

Run this script to launch manual calibration:
```bash
python lerobot/scripts/control_robot.py calibrate \
    --robot-path lerobot/configs/robot/so100.yaml \
    --robot-overrides '~cameras' --arms main_leader
```


### Teleoperate

**Simple teleop**
Then you are ready to teleoperate your robot! Run this simple script (it won't connect and display the cameras):
```bash
python lerobot/scripts/control_robot.py teleoperate \
    --robot-path lerobot/configs/robot/so100.yaml \
    --robot-overrides '~cameras' \
    --display-cameras 0
```


**Teleop with displaying cameras**
Follow [this guide to setup your cameras](https://github.com/huggingface/lerobot/blob/main/examples/7_get_started_with_real_robot.md#c-add-your-cameras-with-opencvcamera). Then you will be able to display the cameras on your computer while you are teleoperating by running the following code. This is useful to prepare your setup before recording your first dataset.
```bash
python lerobot/scripts/control_robot.py teleoperate \
    --robot-path lerobot/configs/robot/so100.yaml
```

### Record a dataset

Once you're familiar with teleoperation, you can record your first dataset with SO-100.

If you want to use the Hugging Face hub features for uploading your dataset and you haven't previously done it, make sure you've logged in using a write-access token, which can be generated from the [Hugging Face settings](https://huggingface.co/settings/tokens):
```bash
huggingface-cli login --token ${HUGGINGFACE_TOKEN} --add-to-git-credential
```

Store your Hugging Face repository name in a variable to run these commands:
```bash
HF_USER=$(huggingface-cli whoami | head -n 1)
echo $HF_USER
```

Record 2 episodes and upload your dataset to the hub:
```bash
python lerobot/scripts/control_robot.py record \
    --robot-path lerobot/configs/robot/so100.yaml \
    --fps 30 \
    --repo-id ${HF_USER}/so100_test \
    --tags so100 tutorial \
    --warmup-time-s 5 \
    --episode-time-s 40 \
    --reset-time-s 10 \
    --num-episodes 2 \
    --push-to-hub 1
```

### Visualize a dataset

If you uploaded your dataset to the hub with `--push-to-hub 1`, you can [visualize your dataset online](https://huggingface.co/spaces/lerobot/visualize_dataset) by copy pasting your repo id given by:
```bash
echo ${HF_USER}/so100_test
```

If you didn't upload with `--push-to-hub 0`, you can also visualize it locally with:
```bash
python lerobot/scripts/visualize_dataset_html.py \
  --repo-id ${HF_USER}/so100_test
```

  <div align="center">
      <img width={800} 
      src="https://files.seeedstudio.com/wiki/robotics/projects/lerobot/visualize_datasets.png" />
  </div>

### Replay an episode

Now try to replay the first episode on your robot:
```bash
python lerobot/scripts/control_robot.py replay \
    --robot-path lerobot/configs/robot/so100.yaml \
    --fps 30 \
    --repo-id ${HF_USER}/so100_test \
    --episode 0
```

### Train a policy

To train a policy to control your robot, use the `python lerobot/scripts/train.py` script. A few arguments are required. Here is an example command:
```bash
python lerobot/scripts/train.py \
  dataset_repo_id=${HF_USER}/so100_test \
  policy=act_so100_real \
  env=so100_real \
  hydra.run.dir=outputs/train/act_so100_test \
  hydra.job.name=act_so100_test \
  device=cuda \
  wandb.enable=true
```

Let's explain it:
1. We provided the dataset as argument with `dataset_repo_id=${HF_USER}/so100_test`.
2. We provided the policy with `policy=act_so100_real`. This loads configurations from [`lerobot/configs/policy/act_so100_real.yaml`](https://github.com/huggingface/lerobot/blob/main/lerobot/configs/policy/act_so100_real.yaml). Importantly, this policy uses 2 cameras as input `laptop`, `phone`.
3. We provided an environment as argument with `env=so100_real`. This loads configurations from [`lerobot/configs/env/so100_real.yaml`](https://github.com/huggingface/lerobot/blob/main/lerobot/configs/env/so100_real.yaml).
4. We provided `device=cuda` since we are training on a Nvidia GPU, but you can also use `device=mps` if you are using a Mac with Apple silicon, or `device=cpu` otherwise.
5. We provided `wandb.enable=true` to use [Weights and Biases](https://docs.wandb.ai/quickstart) for visualizing training plots. This is optional but if you use it, make sure you are logged in by running `wandb login`.

Training should take several hours. You will find checkpoints in `outputs/train/act_so100_test/checkpoints`.

### Evaluate your policy

You can use the `record` function from [`lerobot/scripts/control_robot.py`](https://github.com/huggingface/lerobot/blob/main/lerobot/scripts/control_robot.py) but with a policy checkpoint as input. For instance, run this command to record 10 evaluation episodes:
```bash
python lerobot/scripts/control_robot.py record \
  --robot-path lerobot/configs/robot/so100.yaml \
  --fps 30 \
  --repo-id ${HF_USER}/eval_act_so100_test \
  --tags so100 tutorial eval \
  --warmup-time-s 5 \
  --episode-time-s 40 \
  --reset-time-s 10 \
  --num-episodes 10 \
  -p outputs/train/act_so100_test/checkpoints/last/pretrained_model
```

As you can see, it's almost the same command as previously used to record your training dataset. Two things changed:
1. There is an additional `-p` argument which indicates the path to your policy checkpoint with  (e.g. `-p outputs/train/eval_so100_test/checkpoints/last/pretrained_model`). You can also use the model repository if you uploaded a model checkpoint to the hub (e.g. `-p ${HF_USER}/act_so100_test`).
2. The name of dataset begins by `eval` to reflect that you are running inference (e.g. `--repo-id ${HF_USER}/eval_act_so100_test`).



### Citation
TheRobotStudio Project: [SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100)

Huggingface Project: [Lerobot](https://github.com/huggingface/lerobot/tree/main)

Dnsty: [Jetson Containers](https://github.com/dusty-nv/jetson-containers/tree/master/packages/robots/lerobot)

[Jetson AI Lab](https://www.jetson-ai-lab.com/lerobot.html)

[Diffusion Policy](https://diffusion-policy.cs.columbia.edu/)

[ACT or ALOHA](https://tonyzhaozh.github.io/aloha/)

[TDMPC](https://www.nicklashansen.com/td-mpc/)

[VQ-BeT](https://sjlee.cc/vq-bet/)

## Tech Support & Product Discussion

Thank you for choosing our products! We are here to provide you with different support to ensure that your experience with our products is as smooth as possible. We offer several communication channels to cater to different preferences and needs.

<div class="button_tech_support_container">
<a href="https://forum.seeedstudio.com/" class="button_forum"></a> 
<a href="https://www.seeedstudio.com/contacts" class="button_email"></a>
</div>

<div class="button_tech_support_container">
<a href="https://discord.gg/eWkprNDMU7" class="button_discord"></a> 
<a href="https://github.com/Seeed-Studio/wiki-documents/discussions/69" class="button_discussion"></a>
</div>