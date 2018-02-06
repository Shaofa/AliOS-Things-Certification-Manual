# AliOS Things 认证指南

---

## 1. AliOS Things认证框架

![](/assets/certificate_framework.png)

## 2. AliOS Things API 兼容性认证指南

AliOS Things API兼容性测试是为了保证AliOS Things移植到不同硬件平台后保持良好的兼容性，AliOS Things提供API兼容性测试用例集，用户将用例集移植到硬件平台后，通过工具导出API兼容性测试报告。详细测试步骤见下文。

### 2.1 下载测试用例集

[AliOS Things API兼容性测试用例集](https://github.com/alibaba/AliOS-Things/blob/master/test/testcase/certificate_test)随AliOS Things在GitHub开源，用户下载AliOS Things源码后，在`{AliOS-Things-Root}/test/testcase/certificate_test`目录下可以找到测试用例集源码，文件目录结构如下：

```
  .
  |___aos_test.c              # aos_* API测试用例集
  |___rhino_test.c            # krhino_* API测试用例集
  |___certificate_test.mk     # gcc编译使用的Makefile
  |___cutest                  # API测试框架
      |___cut.c
      |___cut.h
```

> `aos_test.c`与`rhino_test.c`功能相同，rhino\_test.c针对只移植了rhino微内核的MCU，通常二者选其一

### 2.2 移植测试用例集

#### 2.2.1 修改测试用例集源码

测试用例集中设置如下配置项，用户可以根据MCU RAM和移植情况修改配置项，各配置项说明如下：

| 配置项 | 配置说明 | 默认配置项 |
| :--- | :--- | :--- |
| SYSINFO\_MCU | 待测MCU型号 | 空（必填） |
| SYSINFO\_ARCH | 待测MCU架构 | 空（必填） |
| SYSINFO\_BORAD | 待测开发板型号 | 空（必填） |
| TEST\_CONFIG\_MM\_ENABLED | 内存管理测试使能 | 1 |
| TEST\_CONFIG\_MALLOC\_MAX\_SIZE | 堆内存分配最大值\(Byte\) | 1024 |
| TEST\_CONFIG\_MALLOC\_FREE\_TIMES | 反复分配/释放堆内存次数 | 100000 |
| TEST\_CONFIG\_TASK\_ENABLED | 任务管理测试使能 | 1 |
| TEST\_CONFIG\_STACK\_SIZE | 任务栈大小\(Byte\) | 1024 |
| TEST\_CONFIG\_MAX\_TASK\_COUNT | 创建最大任务数 | 10 |
| TEST\_CONFIG\_CREATE\_TASK\_TIMES | 反复创建/销毁任务次数 | 10000 |
| TEST\_CONFIG\_TASK\_COMM\_ENABLED | 任务间通信测试使能 | 1 |
| TEST\_CONFIG\_SYNC\_TIMES | 任务间同步次数 | 100000 |
| TEST\_CONFIG\_TIMER\_ENABLED | 定时器测试使能 | 1 |
| TEST\_CONFIG\_KV\_ENABLED | KV测试使能 | 1 |
| TEST\_CONFIG\_KV\_TIMES | 反复读写KV次数 | 10000 |
| TEST\_CONFIG\_YLOOP\_ENABLED | Yloop测试使能 | 1 |
| TEST\_CONFIG\_YLOOP\_EVENT\_COUNT | 注册Yloop事件数量 | 1000 |
| TEST\_CONFIG\_YLOOP\_LOOP\_COUNT | 最大创建Yloop数量 | 10 |

#### 2.2.2 gcc编译

API测试用例集默认使用GCC编译，用户只需要执行以下简单命令就能生成测试固件，编译得到的固件在{AliOS-Things-Root}/out目录下

```
$ aos make yts@{board} test=certificate
```

> 针对只移植了rhino微内核的暂时无法使用gcc编译方式

#### 2.2.3 Keil/IAR编译

API测试用例集默认使用GCC编译，但是可以移植到Keil/IAR工程中，测试用例集的函数调用入口如下：

```cpp
/* 将aos_test.c和cutest 或者 rhino_test.c和cutest 移植到Keil/IAR工程中，并调用该接口 */
void certificate_test(void);
```

### 2.3 导出测试报告



## 3. Wi-Fi SoC 认证指南

## 4. Wi-Fi + MCU 认证指南

## 5. MCU 认证指南

## 6. 蓝牙 SoC 认证指南

## 7. LoRa MCU 认证指南



