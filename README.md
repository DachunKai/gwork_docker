# [ustc gpu-cluster](https://git.ustc.edu.cn/ypb/gpu-cluster) dockerfile
- cu102 build for dgx01/dgx02
- cu113 build for 1080ti/2080ti/3080ti/3090
## Usage
**Recommend!**
- Build local, then upload to DockerHub or AliCloud
- Ask the administrator to help pull the image to G101
- Debug the pulled image on G101. If everything goes well, ask the administrator to publish the image.

**Directly build on G101**
```bash
git clone https://github.com/DachunKai/gwork_docker.git &&
cd ./cu113 &&
ssh g101 &&
sudo docker build -t bit:5000/kaidc_torch10_cu11 .
```
