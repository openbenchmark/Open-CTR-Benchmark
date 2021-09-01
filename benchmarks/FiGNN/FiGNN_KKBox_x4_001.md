## FiGNN_KKBox_x4_001

A notebook to benchmark FiGNN on KKBox_x4_001 dataset.

Author: [XUEPAI Team](https://github.com/xue-pai)


### Index
[Environments](#Environments) | [Dataset](#Dataset) | [Code](#Code) | [Results](#Results) | [Logs](#Logs)

### Environments
+ Hardware

  ```python
  CPU: Intel(R) Xeon(R) CPU E5-2690 v4 @ 2.6GHz
  RAM: 500G+
  ```
+ Software

  ```python
  python: 3.6.5
  pandas: 1.0.0
  numpy: 1.18.1
  ```

### Dataset
In this setting, For all categorical fields, we replace infrequent features with a default <OOV> token by setting the threshold min_category_count=10.

To make a fair comparison, we fix embedding_dim=128, which performs well.


### Code




### Results
```python
[Metrics] logloss: 0.490226 - AUC: 0.846333
```


### Logs
```python
2020-05-02 17:42:26,690 P5831 INFO {
    "batch_size": "2000",
    "dataset_id": "kkbox_x4_001_c5c9c6e3",
    "embedding_dim": "128",
    "embedding_dropout": "0",
    "embedding_regularizer": "0.0001",
    "epochs": "100",
    "every_x_epochs": "1",
    "gnn_layers": "3",
    "learning_rate": "0.001",
    "loss": "binary_crossentropy",
    "metrics": "['logloss', 'AUC']",
    "model": "FiGNN",
    "model_id": "FiGNN_kkbox_x4_005_58c5e171",
    "model_root": "./KKBox/FiGNN_kkbox/",
    "monitor": "{'AUC': 1, 'logloss': -1}",
    "monitor_mode": "max",
    "net_regularizer": "0",
    "optimizer": "adam",
    "patience": "2",
    "pickle_feature_encoder": "True",
    "reuse_graph_layer": "False",
    "save_best_only": "True",
    "seed": "2019",
    "shuffle": "True",
    "task": "binary_classification",
    "use_gru": "True",
    "use_hdf5": "True",
    "use_residual": "True",
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
2020-05-02 17:42:26,691 P5831 INFO Set up feature encoder...
2020-05-02 17:42:26,691 P5831 INFO Load feature_map from json: ../data/KKBox/kkbox_x4_001_c5c9c6e3/feature_map.json
2020-05-02 17:42:26,691 P5831 INFO Loading data...
2020-05-02 17:42:26,694 P5831 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/train.h5
2020-05-02 17:42:28,766 P5831 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/valid.h5
2020-05-02 17:42:29,466 P5831 INFO Train samples: total/5901932, pos/2971724, neg/2930208, ratio/50.35%
2020-05-02 17:42:29,493 P5831 INFO Validation samples: total/737743, pos/371466, neg/366277, ratio/50.35%
2020-05-02 17:42:29,493 P5831 INFO Loading train data done.
2020-05-02 17:42:36,194 P5831 INFO **** Start training: 2951 batches/epoch ****
2020-05-02 18:04:04,502 P5831 INFO [Metrics] logloss: 0.550557 - AUC: 0.790746
2020-05-02 18:04:04,523 P5831 INFO Save best model: monitor(max): 0.240190
2020-05-02 18:04:04,567 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 18:04:04,634 P5831 INFO Train loss: 0.598919
2020-05-02 18:04:04,634 P5831 INFO ************ Epoch=1 end ************
2020-05-02 18:25:32,942 P5831 INFO [Metrics] logloss: 0.534739 - AUC: 0.805514
2020-05-02 18:25:32,963 P5831 INFO Save best model: monitor(max): 0.270775
2020-05-02 18:25:33,030 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 18:25:33,107 P5831 INFO Train loss: 0.569713
2020-05-02 18:25:33,107 P5831 INFO ************ Epoch=2 end ************
2020-05-02 18:47:03,283 P5831 INFO [Metrics] logloss: 0.526928 - AUC: 0.812327
2020-05-02 18:47:03,300 P5831 INFO Save best model: monitor(max): 0.285399
2020-05-02 18:47:03,365 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 18:47:03,423 P5831 INFO Train loss: 0.560505
2020-05-02 18:47:03,423 P5831 INFO ************ Epoch=3 end ************
2020-05-02 19:08:31,435 P5831 INFO [Metrics] logloss: 0.522099 - AUC: 0.816474
2020-05-02 19:08:31,458 P5831 INFO Save best model: monitor(max): 0.294375
2020-05-02 19:08:32,021 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 19:08:32,075 P5831 INFO Train loss: 0.555514
2020-05-02 19:08:32,075 P5831 INFO ************ Epoch=4 end ************
2020-05-02 19:30:01,209 P5831 INFO [Metrics] logloss: 0.518983 - AUC: 0.819045
2020-05-02 19:30:01,230 P5831 INFO Save best model: monitor(max): 0.300062
2020-05-02 19:30:01,296 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 19:30:01,373 P5831 INFO Train loss: 0.552492
2020-05-02 19:30:01,374 P5831 INFO ************ Epoch=5 end ************
2020-05-02 19:51:29,124 P5831 INFO [Metrics] logloss: 0.516556 - AUC: 0.821256
2020-05-02 19:51:29,141 P5831 INFO Save best model: monitor(max): 0.304700
2020-05-02 19:51:29,202 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 19:51:29,287 P5831 INFO Train loss: 0.550314
2020-05-02 19:51:29,287 P5831 INFO ************ Epoch=6 end ************
2020-05-02 20:12:58,735 P5831 INFO [Metrics] logloss: 0.514308 - AUC: 0.823212
2020-05-02 20:12:58,767 P5831 INFO Save best model: monitor(max): 0.308904
2020-05-02 20:12:58,845 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 20:12:58,899 P5831 INFO Train loss: 0.548628
2020-05-02 20:12:58,899 P5831 INFO ************ Epoch=7 end ************
2020-05-02 20:34:27,751 P5831 INFO [Metrics] logloss: 0.512171 - AUC: 0.824753
2020-05-02 20:34:27,769 P5831 INFO Save best model: monitor(max): 0.312583
2020-05-02 20:34:27,835 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 20:34:27,918 P5831 INFO Train loss: 0.547290
2020-05-02 20:34:27,918 P5831 INFO ************ Epoch=8 end ************
2020-05-02 20:55:58,119 P5831 INFO [Metrics] logloss: 0.510956 - AUC: 0.825652
2020-05-02 20:55:58,137 P5831 INFO Save best model: monitor(max): 0.314696
2020-05-02 20:55:58,204 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 20:55:58,262 P5831 INFO Train loss: 0.546054
2020-05-02 20:55:58,262 P5831 INFO ************ Epoch=9 end ************
2020-05-02 21:17:26,716 P5831 INFO [Metrics] logloss: 0.509355 - AUC: 0.827064
2020-05-02 21:17:26,735 P5831 INFO Save best model: monitor(max): 0.317709
2020-05-02 21:17:26,802 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 21:17:26,862 P5831 INFO Train loss: 0.545114
2020-05-02 21:17:26,863 P5831 INFO ************ Epoch=10 end ************
2020-05-02 21:38:56,501 P5831 INFO [Metrics] logloss: 0.507752 - AUC: 0.828349
2020-05-02 21:38:56,519 P5831 INFO Save best model: monitor(max): 0.320598
2020-05-02 21:38:56,580 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 21:38:56,660 P5831 INFO Train loss: 0.544152
2020-05-02 21:38:56,661 P5831 INFO ************ Epoch=11 end ************
2020-05-02 22:00:24,100 P5831 INFO [Metrics] logloss: 0.507250 - AUC: 0.828856
2020-05-02 22:00:24,118 P5831 INFO Save best model: monitor(max): 0.321606
2020-05-02 22:00:24,179 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 22:00:24,253 P5831 INFO Train loss: 0.543100
2020-05-02 22:00:24,253 P5831 INFO ************ Epoch=12 end ************
2020-05-02 22:21:51,516 P5831 INFO [Metrics] logloss: 0.506949 - AUC: 0.829106
2020-05-02 22:21:51,541 P5831 INFO Save best model: monitor(max): 0.322157
2020-05-02 22:21:52,692 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 22:21:52,747 P5831 INFO Train loss: 0.542270
2020-05-02 22:21:52,748 P5831 INFO ************ Epoch=13 end ************
2020-05-02 22:43:19,514 P5831 INFO [Metrics] logloss: 0.505997 - AUC: 0.829738
2020-05-02 22:43:19,539 P5831 INFO Save best model: monitor(max): 0.323742
2020-05-02 22:43:20,283 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 22:43:20,334 P5831 INFO Train loss: 0.541505
2020-05-02 22:43:20,334 P5831 INFO ************ Epoch=14 end ************
2020-05-02 23:04:48,553 P5831 INFO [Metrics] logloss: 0.505346 - AUC: 0.830425
2020-05-02 23:04:48,576 P5831 INFO Save best model: monitor(max): 0.325079
2020-05-02 23:04:48,656 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 23:04:48,725 P5831 INFO Train loss: 0.540810
2020-05-02 23:04:48,726 P5831 INFO ************ Epoch=15 end ************
2020-05-02 23:26:16,602 P5831 INFO [Metrics] logloss: 0.504424 - AUC: 0.831215
2020-05-02 23:26:16,622 P5831 INFO Save best model: monitor(max): 0.326791
2020-05-02 23:26:16,687 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 23:26:16,760 P5831 INFO Train loss: 0.540064
2020-05-02 23:26:16,760 P5831 INFO ************ Epoch=16 end ************
2020-05-02 23:47:45,498 P5831 INFO [Metrics] logloss: 0.504195 - AUC: 0.831542
2020-05-02 23:47:45,518 P5831 INFO Save best model: monitor(max): 0.327347
2020-05-02 23:47:45,579 P5831 INFO --- 2951/2951 batches finished ---
2020-05-02 23:47:45,635 P5831 INFO Train loss: 0.539427
2020-05-02 23:47:45,635 P5831 INFO ************ Epoch=17 end ************
2020-05-03 00:09:12,926 P5831 INFO [Metrics] logloss: 0.503196 - AUC: 0.832344
2020-05-03 00:09:12,950 P5831 INFO Save best model: monitor(max): 0.329148
2020-05-03 00:09:13,041 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 00:09:13,118 P5831 INFO Train loss: 0.538579
2020-05-03 00:09:13,118 P5831 INFO ************ Epoch=18 end ************
2020-05-03 00:30:42,058 P5831 INFO [Metrics] logloss: 0.503209 - AUC: 0.832513
2020-05-03 00:30:42,079 P5831 INFO Save best model: monitor(max): 0.329304
2020-05-03 00:30:42,151 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 00:30:42,204 P5831 INFO Train loss: 0.538078
2020-05-03 00:30:42,204 P5831 INFO ************ Epoch=19 end ************
2020-05-03 00:52:10,258 P5831 INFO [Metrics] logloss: 0.502570 - AUC: 0.833020
2020-05-03 00:52:10,281 P5831 INFO Save best model: monitor(max): 0.330451
2020-05-03 00:52:10,351 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 00:52:10,430 P5831 INFO Train loss: 0.537450
2020-05-03 00:52:10,430 P5831 INFO ************ Epoch=20 end ************
2020-05-03 01:13:38,352 P5831 INFO [Metrics] logloss: 0.502186 - AUC: 0.833270
2020-05-03 01:13:38,374 P5831 INFO Save best model: monitor(max): 0.331084
2020-05-03 01:13:38,437 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 01:13:38,507 P5831 INFO Train loss: 0.536880
2020-05-03 01:13:38,508 P5831 INFO ************ Epoch=21 end ************
2020-05-03 01:35:07,358 P5831 INFO [Metrics] logloss: 0.502711 - AUC: 0.833081
2020-05-03 01:35:07,386 P5831 INFO Monitor(max) STOP: 0.330370 !
2020-05-03 01:35:07,386 P5831 INFO Reduce learning rate on plateau: 0.000100
2020-05-03 01:35:07,387 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 01:35:07,465 P5831 INFO Train loss: 0.536106
2020-05-03 01:35:07,465 P5831 INFO ************ Epoch=22 end ************
2020-05-03 01:56:36,786 P5831 INFO [Metrics] logloss: 0.490364 - AUC: 0.844749
2020-05-03 01:56:36,802 P5831 INFO Save best model: monitor(max): 0.354385
2020-05-03 01:56:36,865 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 01:56:36,917 P5831 INFO Train loss: 0.483694
2020-05-03 01:56:36,917 P5831 INFO ************ Epoch=23 end ************
2020-05-03 02:18:06,756 P5831 INFO [Metrics] logloss: 0.490848 - AUC: 0.846058
2020-05-03 02:18:06,775 P5831 INFO Save best model: monitor(max): 0.355209
2020-05-03 02:18:06,844 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 02:18:06,919 P5831 INFO Train loss: 0.459459
2020-05-03 02:18:06,920 P5831 INFO ************ Epoch=24 end ************
2020-05-03 02:39:33,212 P5831 INFO [Metrics] logloss: 0.494106 - AUC: 0.845933
2020-05-03 02:39:33,237 P5831 INFO Monitor(max) STOP: 0.351827 !
2020-05-03 02:39:33,237 P5831 INFO Reduce learning rate on plateau: 0.000010
2020-05-03 02:39:33,238 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 02:39:33,307 P5831 INFO Train loss: 0.448289
2020-05-03 02:39:33,307 P5831 INFO ************ Epoch=25 end ************
2020-05-03 03:01:02,264 P5831 INFO [Metrics] logloss: 0.500821 - AUC: 0.844863
2020-05-03 03:01:02,282 P5831 INFO Monitor(max) STOP: 0.344042 !
2020-05-03 03:01:02,282 P5831 INFO Reduce learning rate on plateau: 0.000001
2020-05-03 03:01:02,282 P5831 INFO Early stopping at epoch=26
2020-05-03 03:01:02,282 P5831 INFO --- 2951/2951 batches finished ---
2020-05-03 03:01:02,359 P5831 INFO Train loss: 0.428128
2020-05-03 03:01:02,359 P5831 INFO Training finished.
2020-05-03 03:01:02,359 P5831 INFO Load best model: /home/hispace/container/data/xxx/FuxiCTR/benchmarks/KKBox/FiGNN_kkbox/kkbox_x4_001_c5c9c6e3/FiGNN_kkbox_x4_005_58c5e171_kkbox_x4_001_c5c9c6e3_model.ckpt
2020-05-03 03:01:02,436 P5831 INFO ****** Train/validation evaluation ******
2020-05-03 03:09:30,620 P5831 INFO [Metrics] logloss: 0.406920 - AUC: 0.895108
2020-05-03 03:10:33,509 P5831 INFO [Metrics] logloss: 0.490848 - AUC: 0.846058
2020-05-03 03:10:33,621 P5831 INFO ******** Test evaluation ********
2020-05-03 03:10:33,622 P5831 INFO Loading data...
2020-05-03 03:10:33,622 P5831 INFO Loading data from h5: ../data/KKBox/kkbox_x4_001_c5c9c6e3/test.h5
2020-05-03 03:10:33,705 P5831 INFO Test samples: total/737743, pos/371466, neg/366277, ratio/50.35%
2020-05-03 03:10:33,705 P5831 INFO Loading test data done.
2020-05-03 03:11:36,109 P5831 INFO [Metrics] logloss: 0.490226 - AUC: 0.846333


```