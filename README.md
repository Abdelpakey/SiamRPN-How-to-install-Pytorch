
Download from https://github.com/foolwood/DaSiamRPN

Install using :

## How-to-install-Pytorch


For linux, cuda9.0, python3.6:

    pip3 install http://download.pytorch.org/whl/cu90/torch-0.3.1-cp36-cp36m-linux_x86_64.whl

    pip3 install torchvision


For other cuda/python version: check website: https://ptorch.com/news/145.html

Fix Xrange in VOT.py

Go to run_SiamRPN.py

line #31
   insted of 
           anchor = np.tile(anchor, score_size * score_size).reshape((-1, 4))
   Add 
           anchor = np.tile(anchor, int(score_size * score_size)).reshape((-1, 4))
           
 ine #33 & #34
    instead of 
           xx, yy = np.meshgrid([ori + total_stride * dx for dx in range(score_size)],
                         [ori + total_stride * dy for dy in range(score_size)])
     Add
           xx, yy = np.meshgrid([ori + total_stride * dx for dx in range(int(score_size))],
                         [ori + total_stride * dy for dy in range(int(score_size))])
