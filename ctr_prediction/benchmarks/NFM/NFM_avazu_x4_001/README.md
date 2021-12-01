## NFM_Avazu_x4_001 

A notebook to benchmark NFM on Avazu_x4_001 dataset.

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
In this setting, we preprocess the data split by removing the ``id`` field that is useless for CTR prediction. In addition, we transform the timestamp field into three fields: hour, weekday, and is_weekend. For all categorical fields, we filter infrequent features by setting the threshold min_category_count=2 (performs well) and replace them with a default ``<OOV>`` token. Note that we do not follow the exact preprocessing steps in AutoInt, because the authors neither remove the useless ``id`` field nor specially preprocess the timestamp field.

To make a fair comparison, we fix **embedding_dim=16** as with AutoInt.


### Code
1. Install FuxiCTR
  
    Install FuxiCTR via `pip install fuxictr==1.0` to get all dependencies ready. Then download [the FuxiCTR repository](https://github.com/huawei-noah/benchmark/archive/53e314461c19dbc7f462b42bf0f0bfae020dc398.zip) to your local path.

2. Downalod the dataset and run [the preprocessing script](https://github.com/xue-pai/Open-CTR-Benchmark/blob/master/datasets/Avazu/Avazu_x4/split_avazu_x4.py) for data splitting. 

3. Download the hyper-parameter configuration file: [NFM_avazu_x4_tuner_config_01.yaml](./NFM_avazu_x4_tuner_config_01.yaml)

4. Run the following script to reproduce the result. 
  + --config: The config file that defines the tuning space
  + --tag: Specify which expid to run (each expid corresponds to a specific setting of hyper-parameters in the tunner space)
  + --gpu: The available gpus for parameters tuning.

  ```bash
  cd FuxiCTR/benchmarks
  python run_param_tuner.py --config YOUR_PATH/NFM_avazu_x4_tuner_config_01.yaml --tag 009 --gpu 0
  ```


### Results
```python
[Metrics] logloss: 0.374279 - AUC: 0.789390
```


### Logs
```python
2020-06-15 15:37:33,720 P2008 INFO {
    "batch_norm": "False",
    "batch_size": "10000",
    "data_format": "h5",
    "data_root": "../data/Avazu/",
    "dataset_id": "avazu_x4_3bbbc4c9",
    "debug": "False",
    "embedding_dim": "16",
    "embedding_dropout": "0",
    "embedding_regularizer": "1e-09",
    "epochs": "100",
    "every_x_epochs": "1",
    "gpu": "0",
    "hidden_activations": "relu",
    "hidden_units": "[1000, 1000, 1000, 1000]",
    "learning_rate": "0.001",
    "loss": "binary_crossentropy",
    "metrics": "['logloss', 'AUC']",
    "model": "NFM",
    "model_id": "NFM_avazu_x4_3bbbc4c9_009_601b920f",
    "model_root": "./Avazu/NFM_avazu/min2/",
    "monitor": "{'AUC': 1, 'logloss': -1}",
    "monitor_mode": "max",
    "net_dropout": "0",
    "net_regularizer": "0",
    "optimizer": "adam",
    "patience": "2",
    "pickle_feature_encoder": "True",
    "save_best_only": "True",
    "seed": "2019",
    "shuffle": "True",
    "task": "binary_classification",
    "test_data": "../data/Avazu/avazu_x4_3bbbc4c9/test.h5",
    "train_data": "../data/Avazu/avazu_x4_3bbbc4c9/train.h5",
    "use_hdf5": "True",
    "valid_data": "../data/Avazu/avazu_x4_3bbbc4c9/valid.h5",
    "verbose": "0",
    "version": "pytorch",
    "workers": "3"
}
2020-06-15 15:37:33,722 P2008 INFO Set up feature encoder...
2020-06-15 15:37:33,723 P2008 INFO Load feature_map from json: ../data/Avazu/avazu_x4_3bbbc4c9/feature_map.json
2020-06-15 15:37:33,723 P2008 INFO Loading data...
2020-06-15 15:37:33,728 P2008 INFO Loading data from h5: ../data/Avazu/avazu_x4_3bbbc4c9/train.h5
2020-06-15 15:37:36,846 P2008 INFO Loading data from h5: ../data/Avazu/avazu_x4_3bbbc4c9/valid.h5
2020-06-15 15:37:38,083 P2008 INFO Train samples: total/32343172, pos/5492052, neg/26851120, ratio/16.98%
2020-06-15 15:37:38,188 P2008 INFO Validation samples: total/4042897, pos/686507, neg/3356390, ratio/16.98%
2020-06-15 15:37:38,189 P2008 INFO Loading train data done.
2020-06-15 15:37:47,174 P2008 INFO Start training: 3235 batches/epoch
2020-06-15 15:37:47,174 P2008 INFO ************ Epoch=1 start ************
2020-06-15 15:45:31,603 P2008 INFO [Metrics] logloss: 0.374350 - AUC: 0.789300
2020-06-15 15:45:31,607 P2008 INFO Save best model: monitor(max): 0.414951
2020-06-15 15:45:32,031 P2008 INFO --- 3235/3235 batches finished ---
2020-06-15 15:45:32,084 P2008 INFO Train loss: 0.383051
2020-06-15 15:45:32,084 P2008 INFO ************ Epoch=1 end ************
2020-06-15 15:53:15,182 P2008 INFO [Metrics] logloss: 0.380202 - AUC: 0.787004
2020-06-15 15:53:15,188 P2008 INFO Monitor(max) STOP: 0.406801 !
2020-06-15 15:53:15,189 P2008 INFO Reduce learning rate on plateau: 0.000100
2020-06-15 15:53:15,189 P2008 INFO --- 3235/3235 batches finished ---
2020-06-15 15:53:15,244 P2008 INFO Train loss: 0.339664
2020-06-15 15:53:15,244 P2008 INFO ************ Epoch=2 end ************
2020-06-15 16:01:00,486 P2008 INFO [Metrics] logloss: 0.417394 - AUC: 0.775632
2020-06-15 16:01:00,492 P2008 INFO Monitor(max) STOP: 0.358238 !
2020-06-15 16:01:00,492 P2008 INFO Reduce learning rate on plateau: 0.000010
2020-06-15 16:01:00,493 P2008 INFO Early stopping at epoch=3
2020-06-15 16:01:00,493 P2008 INFO --- 3235/3235 batches finished ---
2020-06-15 16:01:00,552 P2008 INFO Train loss: 0.293939
2020-06-15 16:01:00,553 P2008 INFO Training finished.
2020-06-15 16:01:00,553 P2008 INFO Load best model: /cache/xxx/FuxiCTR/benchmarks/Avazu/NFM_avazu/min2/avazu_x4_3bbbc4c9/NFM_avazu_x4_3bbbc4c9_009_601b920f_model.ckpt
2020-06-15 16:01:01,128 P2008 INFO ****** Train/validation evaluation ******
2020-06-15 16:04:03,337 P2008 INFO [Metrics] logloss: 0.344772 - AUC: 0.837206
2020-06-15 16:04:25,373 P2008 INFO [Metrics] logloss: 0.374350 - AUC: 0.789300
2020-06-15 16:04:25,441 P2008 INFO ******** Test evaluation ********
2020-06-15 16:04:25,441 P2008 INFO Loading data...
2020-06-15 16:04:25,441 P2008 INFO Loading data from h5: ../data/Avazu/avazu_x4_3bbbc4c9/test.h5
2020-06-15 16:04:26,097 P2008 INFO Test samples: total/4042898, pos/686507, neg/3356391, ratio/16.98%
2020-06-15 16:04:26,097 P2008 INFO Loading test data done.
2020-06-15 16:04:48,522 P2008 INFO [Metrics] logloss: 0.374279 - AUC: 0.789390
```