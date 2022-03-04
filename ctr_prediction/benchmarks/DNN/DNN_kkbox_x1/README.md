## DNN_kkbox_x1

A hands-on guide to run the DNN model on the KKBox_x1 dataset.

Author: [XUEPAI](https://github.com/xue-pai)

### Index
[Environments](#Environments) | [Dataset](#Dataset) | [Code](#Code) | [Results](#Results) | [Logs](#Logs)

### Environments
+ Hardware

  ```python
  CPU: Intel(R) Xeon(R) CPU E5-2690 v4 @ 2.60GHz
  GPU: Tesla P100 16G
  RAM: 755G

  ```

+ Software

  ```python
  CUDA: 10.0
  python: 3.6.5
  pytorch: 1.0.1.post2
  pandas: 0.23.0
  numpy: 1.18.1
  scipy: 1.1.0
  sklearn: 0.23.1
  pyyaml: 5.1
  h5py: 2.7.1
  tqdm: 4.59.0
  fuxictr: 1.0.2
  ```

### Dataset
Dataset ID: [KKBox_x1](https://github.com/openbenchmark/BARS/blob/master/ctr_prediction/datasets/KKBox/README.md#KKBox_x1). Please refer to the dataset details to get data ready.

### Code

We use [FuxiCTR-v1.0.2](https://github.com/xue-pai/FuxiCTR/tree/v1.0.2) for this experiment. See the model code: [DNN](https://github.com/xue-pai/FuxiCTR/blob/v1.0.2/fuxictr/pytorch/models/DNN.py).

Running steps:

1. Download [FuxiCTR-v1.0.2](https://github.com/xue-pai/FuxiCTR/archive/refs/tags/v1.0.2.zip) and install all the dependencies listed in the [environments](#environments). Then modify [run_expid.py](./run_expid.py#L5) to add the FuxiCTR library to system path
    
    ```python
    sys.path.append('YOUR_PATH_TO_FuxiCTR/')
    ```

2. Create a data directory and put the downloaded csv files in `../data/Avazu/Avazu_x1`.

3. Both `dataset_config.yaml` and `model_config.yaml` files are available in [DNN_kkbox_x1_tuner_config_02](./DNN_kkbox_x1_tuner_config_02). Make sure the data paths in `dataset_config.yaml` are correctly set to what we create in the last step.

4. Run the following script to start.

    ```bash
    cd DNN_kkbox_x1
    nohup python run_expid.py --config ./DNN_kkbox_x1_tuner_config_02 --expid DNN_kkbox_x1_013_fb9ab73c --gpu 0 > run.log &
    tail -f run.log
    ```

### Results

| logloss | AUC  |
|:--------------------:|:--------------------:|
| 0.480374 | 0.850474  |


### Logs
```python
2020-04-20 14:24:22,914 P17397 INFO {
    "batch_norm": "False",
    "batch_size": "10000",
    "dataset_id": "kkbox_x4_001_c5c9c6e3",
    "embedding_dim": "128",
    "embedding_dropout": "0",
    "embedding_regularizer": "0.0005",
    "epochs": "100",
    "every_x_epochs": "1",
    "hidden_activations": "relu",
    "hidden_units": "[1000, 1000]",
    "learning_rate": "0.001",
    "loss": "binary_crossentropy",
    "metrics": "['logloss', 'AUC']",
    "model": "DNN",
    "model_id": "DNN_kkbox_x4_013_23a8ff2d",
    "model_root": "./KKBox/DNN_kkbox/",
    "monitor": "{'AUC': 1, 'logloss': -1}",
    "monitor_mode": "max",
    "net_dropout": "0.2",
    "net_regularizer": "0",
    "optimizer": "adam",
    "patience": "2",
    "pickle_feature_encoder": "True",
    "save_best_only": "True",
    "seed": "2019",
    "shuffle": "True",
    "task": "binary_classification",
    "use_hdf5": "True",
    "verbose": "0",
    "workers": "3",
    "data_format": "h5",
    "data_root": "../data/KKBox/",
    "test_data": "../data/KKBox/kkbox_x4_001_c5c9c6e3/test.h5",
    "train_data": "../data/KKBox/kkbox_x4_001_c5c9c6e3/train.h5",
    "valid_data": "../data/KKBox/kkbox_x4_001_c5c9c6e3/valid.h5",
    "version": "pytorch",
    "gpu": "1"
}
2020-04-20 14:24:22,915 P17397 INFO Set up feature encoder...
2020-04-20 14:24:22,915 P17397 INFO Load feature_map from json: ../data/KKBox/kkbox_x4_001_c5c9c6e3/feature_map.json
2020-04-20 14:24:22,916 P17397 INFO Loading data...
2020-04-20 14:24:22,917 P17397 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/train.h5
2020-04-20 14:24:23,208 P17397 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/valid.h5
2020-04-20 14:24:23,400 P17397 INFO Train samples: total/5901932, pos/2971724, neg/2930208, ratio/50.35%
2020-04-20 14:24:23,420 P17397 INFO Validation samples: total/737743, pos/371466, neg/366277, ratio/50.35%
2020-04-20 14:24:23,420 P17397 INFO Loading train data done.
2020-04-20 14:24:28,271 P17397 INFO **** Start training: 591 batches/epoch ****
2020-04-20 14:26:19,878 P17397 INFO [Metrics] logloss: 0.557521 - AUC: 0.784916
2020-04-20 14:26:19,895 P17397 INFO Save best model: monitor(max): 0.227395
2020-04-20 14:26:20,038 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:26:20,075 P17397 INFO Train loss: 0.610812
2020-04-20 14:26:20,075 P17397 INFO ************ Epoch=1 end ************
2020-04-20 14:28:14,621 P17397 INFO [Metrics] logloss: 0.542711 - AUC: 0.798374
2020-04-20 14:28:14,639 P17397 INFO Save best model: monitor(max): 0.255663
2020-04-20 14:28:14,801 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:28:14,845 P17397 INFO Train loss: 0.592240
2020-04-20 14:28:14,846 P17397 INFO ************ Epoch=2 end ************
2020-04-20 14:30:07,744 P17397 INFO [Metrics] logloss: 0.536235 - AUC: 0.804220
2020-04-20 14:30:07,755 P17397 INFO Save best model: monitor(max): 0.267985
2020-04-20 14:30:07,903 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:30:07,948 P17397 INFO Train loss: 0.585233
2020-04-20 14:30:07,949 P17397 INFO ************ Epoch=3 end ************
2020-04-20 14:31:58,680 P17397 INFO [Metrics] logloss: 0.530583 - AUC: 0.809332
2020-04-20 14:31:58,692 P17397 INFO Save best model: monitor(max): 0.278749
2020-04-20 14:31:58,844 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:31:58,887 P17397 INFO Train loss: 0.581365
2020-04-20 14:31:58,887 P17397 INFO ************ Epoch=4 end ************
2020-04-20 14:33:36,323 P17397 INFO [Metrics] logloss: 0.526339 - AUC: 0.813022
2020-04-20 14:33:36,334 P17397 INFO Save best model: monitor(max): 0.286683
2020-04-20 14:33:36,490 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:33:36,531 P17397 INFO Train loss: 0.578547
2020-04-20 14:33:36,531 P17397 INFO ************ Epoch=5 end ************
2020-04-20 14:35:26,531 P17397 INFO [Metrics] logloss: 0.522226 - AUC: 0.816337
2020-04-20 14:35:26,549 P17397 INFO Save best model: monitor(max): 0.294111
2020-04-20 14:35:26,652 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:35:26,700 P17397 INFO Train loss: 0.575695
2020-04-20 14:35:26,700 P17397 INFO ************ Epoch=6 end ************
2020-04-20 14:37:17,026 P17397 INFO [Metrics] logloss: 0.520301 - AUC: 0.817974
2020-04-20 14:37:17,043 P17397 INFO Save best model: monitor(max): 0.297673
2020-04-20 14:37:17,125 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:37:17,178 P17397 INFO Train loss: 0.573639
2020-04-20 14:37:17,178 P17397 INFO ************ Epoch=7 end ************
2020-04-20 14:39:07,049 P17397 INFO [Metrics] logloss: 0.517508 - AUC: 0.820290
2020-04-20 14:39:07,062 P17397 INFO Save best model: monitor(max): 0.302782
2020-04-20 14:39:07,219 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:39:07,261 P17397 INFO Train loss: 0.571877
2020-04-20 14:39:07,261 P17397 INFO ************ Epoch=8 end ************
2020-04-20 14:40:58,613 P17397 INFO [Metrics] logloss: 0.515722 - AUC: 0.821828
2020-04-20 14:40:58,625 P17397 INFO Save best model: monitor(max): 0.306105
2020-04-20 14:40:58,707 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:40:58,764 P17397 INFO Train loss: 0.570430
2020-04-20 14:40:58,764 P17397 INFO ************ Epoch=9 end ************
2020-04-20 14:42:49,615 P17397 INFO [Metrics] logloss: 0.514218 - AUC: 0.822914
2020-04-20 14:42:49,629 P17397 INFO Save best model: monitor(max): 0.308696
2020-04-20 14:42:49,717 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:42:49,763 P17397 INFO Train loss: 0.569268
2020-04-20 14:42:49,763 P17397 INFO ************ Epoch=10 end ************
2020-04-20 14:44:39,409 P17397 INFO [Metrics] logloss: 0.512540 - AUC: 0.824462
2020-04-20 14:44:39,427 P17397 INFO Save best model: monitor(max): 0.311922
2020-04-20 14:44:39,521 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:44:39,575 P17397 INFO Train loss: 0.568280
2020-04-20 14:44:39,575 P17397 INFO ************ Epoch=11 end ************
2020-04-20 14:46:25,751 P17397 INFO [Metrics] logloss: 0.511315 - AUC: 0.825404
2020-04-20 14:46:25,769 P17397 INFO Save best model: monitor(max): 0.314089
2020-04-20 14:46:25,860 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:46:25,905 P17397 INFO Train loss: 0.567473
2020-04-20 14:46:25,905 P17397 INFO ************ Epoch=12 end ************
2020-04-20 14:48:16,109 P17397 INFO [Metrics] logloss: 0.510442 - AUC: 0.826268
2020-04-20 14:48:16,121 P17397 INFO Save best model: monitor(max): 0.315827
2020-04-20 14:48:16,214 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:48:16,259 P17397 INFO Train loss: 0.566659
2020-04-20 14:48:16,259 P17397 INFO ************ Epoch=13 end ************
2020-04-20 14:50:06,548 P17397 INFO [Metrics] logloss: 0.509651 - AUC: 0.826840
2020-04-20 14:50:06,564 P17397 INFO Save best model: monitor(max): 0.317189
2020-04-20 14:50:06,646 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:50:06,702 P17397 INFO Train loss: 0.565885
2020-04-20 14:50:06,702 P17397 INFO ************ Epoch=14 end ************
2020-04-20 14:52:00,236 P17397 INFO [Metrics] logloss: 0.508113 - AUC: 0.827864
2020-04-20 14:52:00,254 P17397 INFO Save best model: monitor(max): 0.319751
2020-04-20 14:52:00,414 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:52:00,457 P17397 INFO Train loss: 0.565236
2020-04-20 14:52:00,458 P17397 INFO ************ Epoch=15 end ************
2020-04-20 14:53:51,228 P17397 INFO [Metrics] logloss: 0.507882 - AUC: 0.828172
2020-04-20 14:53:51,243 P17397 INFO Save best model: monitor(max): 0.320290
2020-04-20 14:53:51,373 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:53:51,421 P17397 INFO Train loss: 0.564705
2020-04-20 14:53:51,421 P17397 INFO ************ Epoch=16 end ************
2020-04-20 14:55:42,278 P17397 INFO [Metrics] logloss: 0.506679 - AUC: 0.829043
2020-04-20 14:55:42,293 P17397 INFO Save best model: monitor(max): 0.322363
2020-04-20 14:55:42,455 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:55:42,499 P17397 INFO Train loss: 0.564149
2020-04-20 14:55:42,499 P17397 INFO ************ Epoch=17 end ************
2020-04-20 14:57:19,722 P17397 INFO [Metrics] logloss: 0.506046 - AUC: 0.829592
2020-04-20 14:57:19,735 P17397 INFO Save best model: monitor(max): 0.323545
2020-04-20 14:57:19,893 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:57:19,936 P17397 INFO Train loss: 0.563444
2020-04-20 14:57:19,936 P17397 INFO ************ Epoch=18 end ************
2020-04-20 14:59:10,063 P17397 INFO [Metrics] logloss: 0.505300 - AUC: 0.830175
2020-04-20 14:59:10,081 P17397 INFO Save best model: monitor(max): 0.324876
2020-04-20 14:59:10,165 P17397 INFO --- 591/591 batches finished ---
2020-04-20 14:59:10,225 P17397 INFO Train loss: 0.562772
2020-04-20 14:59:10,226 P17397 INFO ************ Epoch=19 end ************
2020-04-20 15:01:01,286 P17397 INFO [Metrics] logloss: 0.504855 - AUC: 0.830567
2020-04-20 15:01:01,304 P17397 INFO Save best model: monitor(max): 0.325712
2020-04-20 15:01:01,469 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:01:01,515 P17397 INFO Train loss: 0.562214
2020-04-20 15:01:01,515 P17397 INFO ************ Epoch=20 end ************
2020-04-20 15:02:52,212 P17397 INFO [Metrics] logloss: 0.504050 - AUC: 0.831195
2020-04-20 15:02:52,224 P17397 INFO Save best model: monitor(max): 0.327145
2020-04-20 15:02:52,306 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:02:52,359 P17397 INFO Train loss: 0.561755
2020-04-20 15:02:52,359 P17397 INFO ************ Epoch=21 end ************
2020-04-20 15:04:42,420 P17397 INFO [Metrics] logloss: 0.503890 - AUC: 0.831715
2020-04-20 15:04:42,434 P17397 INFO Save best model: monitor(max): 0.327825
2020-04-20 15:04:42,587 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:04:42,630 P17397 INFO Train loss: 0.561540
2020-04-20 15:04:42,630 P17397 INFO ************ Epoch=22 end ************
2020-04-20 15:06:33,826 P17397 INFO [Metrics] logloss: 0.503338 - AUC: 0.831828
2020-04-20 15:06:33,849 P17397 INFO Save best model: monitor(max): 0.328490
2020-04-20 15:06:34,013 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:06:34,064 P17397 INFO Train loss: 0.561163
2020-04-20 15:06:34,064 P17397 INFO ************ Epoch=23 end ************
2020-04-20 15:08:11,094 P17397 INFO [Metrics] logloss: 0.502718 - AUC: 0.832363
2020-04-20 15:08:11,108 P17397 INFO Save best model: monitor(max): 0.329645
2020-04-20 15:08:11,232 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:08:11,278 P17397 INFO Train loss: 0.560692
2020-04-20 15:08:11,278 P17397 INFO ************ Epoch=24 end ************
2020-04-20 15:10:05,720 P17397 INFO [Metrics] logloss: 0.502378 - AUC: 0.832539
2020-04-20 15:10:05,738 P17397 INFO Save best model: monitor(max): 0.330161
2020-04-20 15:10:05,899 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:10:05,944 P17397 INFO Train loss: 0.560319
2020-04-20 15:10:05,945 P17397 INFO ************ Epoch=25 end ************
2020-04-20 15:11:57,179 P17397 INFO [Metrics] logloss: 0.501375 - AUC: 0.833321
2020-04-20 15:11:57,191 P17397 INFO Save best model: monitor(max): 0.331946
2020-04-20 15:11:57,263 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:11:57,328 P17397 INFO Train loss: 0.559950
2020-04-20 15:11:57,328 P17397 INFO ************ Epoch=26 end ************
2020-04-20 15:13:49,515 P17397 INFO [Metrics] logloss: 0.501079 - AUC: 0.833417
2020-04-20 15:13:49,533 P17397 INFO Save best model: monitor(max): 0.332338
2020-04-20 15:13:49,626 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:13:49,682 P17397 INFO Train loss: 0.559563
2020-04-20 15:13:49,683 P17397 INFO ************ Epoch=27 end ************
2020-04-20 15:15:42,257 P17397 INFO [Metrics] logloss: 0.500985 - AUC: 0.833573
2020-04-20 15:15:42,270 P17397 INFO Save best model: monitor(max): 0.332588
2020-04-20 15:15:42,396 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:15:42,440 P17397 INFO Train loss: 0.559101
2020-04-20 15:15:42,440 P17397 INFO ************ Epoch=28 end ************
2020-04-20 15:17:32,091 P17397 INFO [Metrics] logloss: 0.500667 - AUC: 0.833906
2020-04-20 15:17:32,105 P17397 INFO Save best model: monitor(max): 0.333238
2020-04-20 15:17:32,212 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:17:32,265 P17397 INFO Train loss: 0.558654
2020-04-20 15:17:32,265 P17397 INFO ************ Epoch=29 end ************
2020-04-20 15:19:10,012 P17397 INFO [Metrics] logloss: 0.500152 - AUC: 0.834270
2020-04-20 15:19:10,030 P17397 INFO Save best model: monitor(max): 0.334118
2020-04-20 15:19:10,187 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:19:10,230 P17397 INFO Train loss: 0.558242
2020-04-20 15:19:10,230 P17397 INFO ************ Epoch=30 end ************
2020-04-20 15:21:01,501 P17397 INFO [Metrics] logloss: 0.499858 - AUC: 0.834475
2020-04-20 15:21:01,519 P17397 INFO Save best model: monitor(max): 0.334617
2020-04-20 15:21:01,676 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:21:01,721 P17397 INFO Train loss: 0.558105
2020-04-20 15:21:01,721 P17397 INFO ************ Epoch=31 end ************
2020-04-20 15:22:52,423 P17397 INFO [Metrics] logloss: 0.500216 - AUC: 0.834343
2020-04-20 15:22:52,437 P17397 INFO Monitor(max) STOP: 0.334127 !
2020-04-20 15:22:52,437 P17397 INFO Reduce learning rate on plateau: 0.000100
2020-04-20 15:22:52,438 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:22:52,490 P17397 INFO Train loss: 0.557846
2020-04-20 15:22:52,490 P17397 INFO ************ Epoch=32 end ************
2020-04-20 15:24:44,192 P17397 INFO [Metrics] logloss: 0.484730 - AUC: 0.846318
2020-04-20 15:24:44,210 P17397 INFO Save best model: monitor(max): 0.361589
2020-04-20 15:24:44,375 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:24:44,417 P17397 INFO Train loss: 0.504638
2020-04-20 15:24:44,417 P17397 INFO ************ Epoch=33 end ************
2020-04-20 15:26:34,433 P17397 INFO [Metrics] logloss: 0.481259 - AUC: 0.849054
2020-04-20 15:26:34,445 P17397 INFO Save best model: monitor(max): 0.367794
2020-04-20 15:26:34,533 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:26:34,593 P17397 INFO Train loss: 0.479852
2020-04-20 15:26:34,593 P17397 INFO ************ Epoch=34 end ************
2020-04-20 15:28:25,054 P17397 INFO [Metrics] logloss: 0.480181 - AUC: 0.850126
2020-04-20 15:28:25,073 P17397 INFO Save best model: monitor(max): 0.369945
2020-04-20 15:28:25,240 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:28:25,284 P17397 INFO Train loss: 0.469942
2020-04-20 15:28:25,285 P17397 INFO ************ Epoch=35 end ************
2020-04-20 15:30:06,657 P17397 INFO [Metrics] logloss: 0.480340 - AUC: 0.850430
2020-04-20 15:30:06,677 P17397 INFO Save best model: monitor(max): 0.370090
2020-04-20 15:30:06,812 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:30:06,857 P17397 INFO Train loss: 0.463377
2020-04-20 15:30:06,857 P17397 INFO ************ Epoch=36 end ************
2020-04-20 15:31:58,102 P17397 INFO [Metrics] logloss: 0.481107 - AUC: 0.850495
2020-04-20 15:31:58,122 P17397 INFO Monitor(max) STOP: 0.369387 !
2020-04-20 15:31:58,123 P17397 INFO Reduce learning rate on plateau: 0.000010
2020-04-20 15:31:58,123 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:31:58,185 P17397 INFO Train loss: 0.457975
2020-04-20 15:31:58,185 P17397 INFO ************ Epoch=37 end ************
2020-04-20 15:33:49,067 P17397 INFO [Metrics] logloss: 0.485654 - AUC: 0.850144
2020-04-20 15:33:49,136 P17397 INFO Monitor(max) STOP: 0.364490 !
2020-04-20 15:33:49,137 P17397 INFO Reduce learning rate on plateau: 0.000001
2020-04-20 15:33:49,137 P17397 INFO Early stopping at epoch=38
2020-04-20 15:33:49,137 P17397 INFO --- 591/591 batches finished ---
2020-04-20 15:33:49,199 P17397 INFO Train loss: 0.438357
2020-04-20 15:33:49,200 P17397 INFO Training finished.
2020-04-20 15:33:49,200 P17397 INFO Load best model: /home/XXX/FuxiCTR/benchmarks/KKBox/DNN_kkbox/kkbox_x4_001_c5c9c6e3/DNN_kkbox_x4_013_23a8ff2d_kkbox_x4_001_c5c9c6e3_model.ckpt
2020-04-20 15:33:49,590 P17397 INFO ****** Train/validation evaluation ******
2020-04-20 15:34:48,782 P17397 INFO [Metrics] logloss: 0.403224 - AUC: 0.898488
2020-04-20 15:34:56,927 P17397 INFO [Metrics] logloss: 0.480340 - AUC: 0.850430
2020-04-20 15:34:57,028 P17397 INFO ******** Test evaluation ********
2020-04-20 15:34:57,028 P17397 INFO Loading data...
2020-04-20 15:34:57,028 P17397 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/test.h5
2020-04-20 15:34:57,115 P17397 INFO Test samples: total/737743, pos/371466, neg/366277, ratio/50.35%
2020-04-20 15:34:57,115 P17397 INFO Loading test data done.
2020-04-20 15:35:04,697 P17397 INFO [Metrics] logloss: 0.480374 - AUC: 0.850474

```