教程
http://www.weixueyuan.net/cpp/rumen/  ()









4其他
4.1延时
（1）_sleep()函数
#include <iostream>
using   namespace   std; 
#include<windows.h>

Sleep(5*1000)；//延时5秒 

Delay( int  time ）函数 
（2）
#include <ctime> 

void Delay(int time)//time*1000为秒数 
{ 
clock_t now = clock(); 
while( clock() - now < time ); 
}

Delay(5*1000);   //延时5秒 

4.2内存
（1）申请内存
float *NHog= (float*)malloc(sizeof(float)* DIM_FEATURE_HOG);

free(NHog);


4.3计时
double exec_time = (double)getTickCount();
face_det_status = face_detection(gray_img, &face_loc);
exec_time = ((double)getTickCount() - exec_time)*1000. /getTickFrequency();
printf(" Time %fms\n", exec_time);



程序运行结束，不退出cmd窗口
 system("pause");
getchar();







4.4宏
（1）注释
# if 0
face_recognition();
# endif


#define CAMERA_MODEL  // 宏定义了 CAMERA_MODEL 虽然没有任何值

#ifdef CAMERA_MODEL
face_recognition();
#else
face_recognition();
#endif

#ifndef CAMERA_MODEL
face_recognition();
#else
face_recognition();
#endif

（2）头文件
#ifndef _EXPAND_FACE_H_
#define _EXPAND_FACE_H_

/********************************************************************
*头文件
*********************************************************************/
#include <stdio.h>
#include <cstring>  
#include <string>  
#include <vector>
#include <cv.h>
#include <highgui.h>
#include <opencv2/opencv.hpp>
#include <time.h>
#include <direct.h>

using namespace cv;
using namespace std;


#include "add_Glass.h"
#include "../eye_detection.h"
#include "../face_alignment.h"
/********************************************************************
*宏定义
*********************************************************************/

/********************************************************************
*结构体定义
*********************************************************************/

/********************************************************************
*函数声明
*********************************************************************/

void get_rotate_240(IplImage *rotate_img_240);


#endif





4.5反正切函数
Eye_degree= -atan(d_eye_y/d_eye_x)*57.3;  // 眼睛角度

4.6bat/sh
（1）bat
CSample.exe  -info Img.dat  -w 24  -h 24
pause


#include <cstdio>
#include <cstring>
#include <cstdlib>
#include <cmath>
#include <ctime>

using namespace std;

#include "utility.hpp"

int main( int argc, char* argv[] )
{
char* infoname   = NULL; /* file name with marked up image descriptions */
    int width  = 24;
    int height = 24;

    for(int i = 1; i < argc; ++i )
    {
        if( !strcmp( argv[i], "-info" ) )
        {
            infoname = argv[++i];
        }
        else if( !strcmp( argv[i], "-w" ) )
        {
            width = atoi( argv[++i] );
        }
        else if( !strcmp( argv[i], "-h" ) )
        {
            height = atoi( argv[++i] );
        }
    }

    printf( "Info file name: %s\n", infoname );
    printf( "Width: %d\n", width );
    printf( "Height: %d\n", height );

    cvCreateTrainingSamples( vecname, width, height );

    printf( "Done\n" );

    return 0;
}


4.7反射
C++没有反射，不能拿到类名



HYPERLINK http://www.cnblogs.com/foundkey/p/5956364.html normalLink <VS>MFC程序显示命令行窗口
编写MFC程序时，想打印出调试信息，使用cout后，发现程序并没有像想象中那样自动弹出命令行窗口，要输出的信息也没地方去查看。百度后知道要手动调出命令行窗口，才可以看到输出的信息。
 
百度上介绍了两种方法，一种是通过添加代码，在程序中建立命令行窗口的对象。这里介绍一种比较简单的方法。
 
右键解决方案，打开属性页。
选择生成事件（build event）->生成后事件（post-build event）->命令行（command line），输入：
1.editbin /SUBSYSTEM:CONSOLE $(OUTDIR)\$(TargetFileName)


$(ProjectDir)
ProjectDir代表包含xxx.sln的路径，如E:\code\MyMoonWarrior-master\proj.win32\Demo5.sln，
ProjectDir的值为E:\code\MyMoonWarrior-master\proj.win32\
$(ProjectDir)../代表工程目录的上层目录，即E:\code\MyMoonWarrior-master\
以此类推$(ProjectDir)../../代表E:\code\



选中Word文档选中部位上方所有字的方法：
方法1：
按Shift + PageUp组合键；
方法2：
按Ctrl + Shift + Home组合键。

同理选中Word文档选中部位下方所有字的方法：
方法1：
按Shift + PageDowe组合键；
方法2：
按Ctrl + Shift + End组合键。




C语言中_exit(),exit(0)与exit(1)有什么区别
 exit(0)表示正常退出 
一般0为正常推出，其它数字1,-1为异常，其对应的错误可以自己指定。
exit()将缓冲区的数据写完后才能退出来，所以调用exit()函数后程序并不会马上退出，这就是有些出现的僵尸程序，而_exit是直接退出进入到内核中去。


C++工具：
（1）valgrind 工具包
虚拟机中执行，速度慢20x。
Memcheck   内存检查

（2） AddressSantitizer 
GCC   内存检查



Cuda
关键词：核函数（Kernel）、线程网格（Grid）、线程块（Block）、线程束（Warp）、线程（Thread）

https://zhuanlan.zhihu.com/p/34587739

在给出CUDA的编程实例之前，这里先对CUDA编程模型中的一些概念及基础知识做个简单介绍。CUDA编程模型是一个异构模型，需要CPU和GPU协同工作。在CUDA中，host和device是两个重要的概念，我们用host指代CPU及其内存，而用device指代GPU及其内存。CUDA程序中既包含host程序，又包含device程序，它们分别在CPU和GPU上运行。同时，host与device之间可以进行通信，这样它们之间可以进行数据拷贝。典型的CUDA程序的执行流程如下：
1)分配host内存，并进行数据初始化；
2)分配device内存，并从host将数据拷贝到device上；
3)调用CUDA的核函数在device上完成指定的运算；
4)将device上的运算结果拷贝到host上；
5)释放device和host上分配的内存。
























C++ 指针类型：
指针类型   &buf[0]   &buf

常引用 和 应用：
常引用不能修改 引用变量的值，无写权限。
应用 可以修改，有读写权限

https://www.cnblogs.com/yang666/p/6546966.html 


有继承关系的子类，对应对象，析构函数需要是虚函数



《深入理解计算机系统》
《》
