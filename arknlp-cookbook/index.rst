欢迎使用ark-nlp
==================

`ark-nlp <https://github.com/xiangking/ark-nlp>`_ 是DataArk开源的中文自然语言处理开发库，旨在收集和复现学术与工作中常用的NLP模型并整合成方便调用的形式，从而帮助NLPer快速进行实验对比和比赛应用。

* 项目GitHub: https://github.com/xiangking/ark-nlp
* GitHub Issue反馈: https://github.com/xiangking/ark-nlp/issues
* 公众号：DataArk
* wechat ID: fk95624

.. toctree::
   :maxdepth: 1
   :caption: 快速开始

   安装 <get_started/installation>
   快速实现医疗文本分类 <get_started/quick_start>

.. toctree::
   :maxdepth: 1
   :caption: API Reference
   
   ark_nlp.model按实际NLP任务封装常用的模型，方便调用 <source/ark_nlp.model>
   ark_nlp.dataset封装数据加载、处理和转化等功能 <source/ark_nlp.dataset>
   ark_nlp.nn封装一些完整的神经网络模型 <source/ark_nlp.nn>
   ark_nlp.processor封装分词器、词典和构图器等 <source/ark_nlp.processor>
   ark_nlp.factory封装损失函数、优化器、训练和预测等功能 <source/ark_nlp.factory>
   ark_nlp.model.tc文本分类 <source/ark_nlp.model.tc>
   ark_nlp.model.tm文本匹配 <source/ark_nlp.model.tm>
   ark_nlp.model.ner命名实体识别 <source/ark_nlp.model.ner>
   ark_nlp.model.re关系抽取 <source/ark_nlp.model.re>

Indices and tables
====================
* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

