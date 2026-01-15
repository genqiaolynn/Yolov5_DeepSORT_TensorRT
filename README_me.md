## 最近在debug这个仓库
1. 直接clone下来就能运行，我把weights和data都放到仓库里了
2. Makefile是修改过的，检查下库的路径就好了
3. make run

## 文件结构
- Infer、Yolo 和 DeepSORT 使用接口模式和 RAII 进行封装
   - infer.h， yolo.h，deepsort.h 仅暴露 create_* 和推理接口
   - 使用 create_* 创建对象实例，将自动解析 onnx 文件，生成 engine 并加载
- infer.cpp: 分四个线程，两两之间为生产者-消费者关系
  