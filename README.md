# Distributed-storage-system-based-on-the-Raft-algorithm
A distributed key-value (K-V) database based on the Raft consensus algorithm, featuring linearizability and partition tolerance, capable of providing services normally to external clients even when less than half of the nodes fail. 

## 使用方法
### 1.库准备
- muduo
- boost
- protoc
- clang-format（可选）

**安装说明**

- clang-format，如果你不设计提交pr，那么不用安装，这里也给出安装命令:`sudo apt-get install clang-format`
- protoc，本地版本为3.12.4，ubuntu22使用`sudo apt-get install protobuf-compiler libprotobuf-dev`安装默认就是这个版本
- boost，`sudo apt-get install libboost-dev libboost-test-dev libboost-all-dev`
- muduo,https://blog.csdn.net/QIANGWEIYUAN/article/details/89023980

### 2.编译启动
#### 使用rpc
```
mkdir cmake-build-debug
cd cmake-build-debug
cmake ..
make
```
之后在目录bin就有对应的可执行文件生成：
- consumer
- provider
运行即可，注意先运行provider，再运行consumer，原因很简单：需要先提供rpc服务，才能去调用。

#### 使用raft集群
```
mkdir cmake-build-debug
cd cmake-build-debug
cmake..
make
```
之后在目录bin就有对应的可执行文件生成，
```
// make sure you in bin directory ,and this has a test.conf file
raftCoreRun -n 3 -f test.conf
```
