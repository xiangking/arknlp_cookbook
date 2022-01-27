========
快速实现医疗文本分类
========

完整代码和更多例子可参考：https://github.com/xiangking/ark-nlp/tree/main/example

1. 安装ark-nlp
========

安装相关过程和问题可以参考ark-nlp的安装说明。

.. code-block::

    pip install --upgrade ark-nlp

2. 实验数据下载
========

访问 阿里天池的中文医疗信息处理挑战榜_ 下载临床试验筛选标准短文本分类（CHIP-CTC）

.. _阿里天池的中文医疗信息处理挑战榜: https://tianchi.aliyun.com/dataset/dataDetail?dataId=95414

3. 数据读入
========

.. code-block::

    import pandas as pd
    from ark_nlp.model.tc.bert import Dataset

    train_data_df = pd.read_json(train_data_path)
    train_data_df = (train_data_df.loc[:,['text', 'label']])
    
    dev_data_df = pd.read_json(dev_data_path)
    dev_data_df = (dev_data_df.loc[:,['text', 'label']])

    tc_train_dataset = Dataset(train_data_df)
    tc_dev_dataset = Dataset(dev_data_df)

4. 调用Tokenizer进行数据处理
========

Tokenizer用于将原始输入文本转化成模型可以接受的输入数据形式。

.. code-block::

    tokenizer = Tokenizer(vocab='nghuyong/ernie-1.0', max_seq_len=30)

    tc_train_dataset.convert_to_ids(tokenizer)
    tc_dev_dataset.convert_to_ids(tokenizer)

5. 模型创建与加载预训练语言模型权重
========

ark-nlp内置了BERT、NEZHA等丰富的预训练模型，并且提供直接Fine-tune的封装，可以快速地完成预训练模型Fine-tune进行文本分类任务。

加载预训练模型ERNIE

.. code-block::

    config = BertConfig.from_pretrained('nghuyong/ernie-1.0',num_labels=class_num)
    dl_module = Bert.from_pretrained('nghuyong/ernie-1.0',config=config)

6. 模型训练与评估
======== 

.. code-block::

    model.fit(tc_train_dataset, 
            tc_dev_dataset,
            lr=2e-5,
            epochs=3, 
            batch_size=batch_size
            )

7. 模型预测
========  

.. code-block::

    from ark_nlp.model.tc.bert import Predictor

    tc_predictor_instance = Predictor(model.module, tokenizer, tc_train_dataset.cat2id)
    tc_predictor_instance.predict_one_sample(text)