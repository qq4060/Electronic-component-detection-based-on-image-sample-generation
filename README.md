# Electronic-component-detection-based-on-image-sample-generation
Wu, H., Lv, Q., Yang, J., Yan, X. and Xu, X. (2022), "Electronic component detection based on image sample generation", Soldering &amp; Surface Mount Technology, Vol. 34 No. 1, pp. 1-7. https://doi.org/10.1108/SSMT-08-2020-0036
this paper's dataset can be found here:https://github.com/qq4060/maskr-cnn-for-inspection

The CYCLGAN part mainly refers to this link https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
We used the COLAB implementation of the author's CYCLGAN code
https://colab.research.google.com/github/junyanz/pytorch-CycleGAN-and-pix2pix/blob/master/CycleGAN.ipynb

The specific experimental operation is as follows
1. In the CycleGAN dataset, you need to replace the code in the train part with: !python train.py --dataroot ./datasets/gangban/ --name gangban --checkpoints_dir/content/pytorch-CycleGAN-and-pix2pix/checks - -model cycle_gan
Among them, gangban is a custom directory. After completing the git part of the code, it is created in the datasets directory. The gangban directory should contain trainA, trainB, testA, and testB. Among them, trainA and testA are the same type of pictures (for example, they are both in the steel plate defects. Scratch picture), similarly trainB and testB are the same kind of pictures. There should be more pictures in the train. Checks is also a custom directory name, which will appear in the content/pytorch-CycleGAN-and-pix2pix directory during the running of the code, which will generate some image information during the training process. If you want to change the number of iterations at runtime, you need to find the train file in the pytorch-CycleGAN-and-pix2pix/options directory, and change the number of the train part.

2. Replace the test code with: !python test.py --dataroot datasets/gangban/testA --name gangban --checkpoints_dir /content/pytorch-CycleGAN-and-pix2pix/checks --model test --no_dropout
The gangban and checks here are the directory names corresponding to the above train part. Before running, you need to pay attention to delete the _A in the latest_net_G_A file in the checks/gangban directory during renaming, and the code should use testA (if modified The one is latest_net_G_B, after removing _B, the code part should use testB). The running results here are saved in the newly generated content/pytorch-CycleGAN-and-pix2pix/checks/result directory. If you want to change the storage location, you need to find the test file in the pytorch-CycleGAN-and-pix2pix/options directory and change the storage location.


CYCLGAN 部分主要参考这个链接https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
我们用到了作者CYCLGAN 代码的COLAB实现
https://colab.research.google.com/github/junyanz/pytorch-CycleGAN-and-pix2pix/blob/master/CycleGAN.ipynb

具体实验操作如下
1.在CycleGAN数据集中，需要将train部分的代码更换成：!python train.py --dataroot ./datasets/gangban/  --name  gangban --checkpoints_dir/content/pytorch-CycleGAN-and-pix2pix/checks --model cycle_gan
其中，gangban 为自定义目录，在完成git部分代码后，在datasets目录下建立，gangban目录下应包含trainA、trainB、testA、testB，其中，trainA与testA为同一类图片（比如都是钢板缺陷中的划痕图片），同理trainB与testB也是同一类图片。train中图片数量应该较多。checks也是自定义的目录名字，在运行代码过程中会出现在content/pytorch-CycleGAN-and-pix2pix目录下，其中会生成一些训练过程中的图像信息。在运行时若想要改变迭代次数，需要在pytorch-CycleGAN-and-pix2pix/options目录下找到train文件，更改train部分数字即可。

2. 将test部分代码更换为：!python test.py --dataroot datasets/gangban/testA --name gangban --checkpoints_dir /content/pytorch-CycleGAN-and-pix2pix/checks --model test --no_dropout
这里的gangban与checks是与上面train部分对应的目录名字，在运行之前，需要注意将checks/gangban目录下的latest_net_G_A文件中的_A在重命名中删除，代码中应该使用的是testA(若修改的是latest_net_G_B,将_B 删除后，代码部分应该使用testB)。这里的运行结果保存在新生成的content/pytorch-CycleGAN-and-pix2pix/checks/result目录下，若想更换存储位置，需要在pytorch-CycleGAN-and-pix2pix/options目录下找到test文件，更改储存位置即可。


