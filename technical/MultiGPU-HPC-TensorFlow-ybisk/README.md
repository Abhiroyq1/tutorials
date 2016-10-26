#### 1) Install TensorFlow 0.10
```
    $ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-0.10.0-cp27-none-linux_x86_64.whl
    $ pip install --user --upgrade $TF_BINARY_URL
    < ssh into a gpu machine >
    $ source /usr/usc/cuda/7.5/setup.sh
    $ source /usr/usc/cuDNN/7.5-v5.1/setup.sh
    $ python
    >>> import tensorflow as tf
```


#### 2) MultiGPU Code:
Generate training data:   parity check
``` $ python generateData.py     ```
  
Train  MultiGPU
```$ python parity.py ```

This example code reads the number of GPUs from 
```
os.environ['CUDA_VISIBLE_DEVICES'] = '0,1'
```

#### 3) Tensorboard
This code also produces a graph in Tensorboard
```
    $ source /usr/usc/cuda/7.5/setup.sh
    $ source /usr/usc/cuDNN/7.5-v5.1/setup.sh
    $ tensorboard --logdir=.
```

If you're not on the machine running tensorboard
```
    $ ssh -L 6006:127.0.0.1:6006 <node>
    $ ssh -L 6006:127.0.0.1:6006 <desktop>
    navigate to http://127.0.0.1:6006
```

![Example Screenshot](ScreenShot.png?raw=true "TensorBoard")