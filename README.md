# RLHF\_instructGPT
Reproduce instructGPT

## Install
```bash
git clone git@github.com:LanXiu-0523/RLHF_instructGPT.git
cd RLHF_instructGPT/

python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
## Download local datafile
```bash
cd RLHF_instructGPT/
sudo apt-get install git-lfs
mkdir datafile
cd datafile/
git lfs install

mkdir Dahoas
cd Dahoas/
git clone https://huggingface.co/datasets/Dahoas/rm-static

mkdir ../facebook
cd ../facebook/
GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/facebook/opt-350m
cd opt-350m/
git lfs pull --include="*.bin"

cd ../
GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/facebook/opt-1.3b
cd opt-1.3b/
git lfs pull --include="*.bin"
```

More：
```
cd RLHF_instructGPT/datafile/Dahoas
git clone https://huggingface.co/datasets/Dahoas/full-hh-rlhf
git clone https://huggingface.co/datasets/Dahoas/synthetic-instruct-gptj-pairwise

cd ../
mkdir yitingxie
cd yitingxie/
git clone https://huggingface.co/datasets/yitingxie/rlhf-reward-datasets
```
```
cd RLHF_instructGPT/datafile/
mkdir meta-llama
cd meta-llama/
GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/meta-llama/Llama-2-7b-hf
cd Llama-2-7b-hf/
git lfs pull --include="*.bin"
```

## Run
```bash
# initial running
bash applications/scripts/mul_mach/apt-install.sh
```
```bash
bash train.sh mul_mach
```

## Acknowledgement
This project is built upon the codebase of [DeepSpeedExamples](https://github.com/microsoft/DeepSpeedExamples). Sincere thanks to Microsoft for their hard work!
