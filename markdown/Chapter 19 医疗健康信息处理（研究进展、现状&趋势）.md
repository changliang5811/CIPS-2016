# Chapter 19 医疗健康信息处理（研究进展、现状&趋势）

## 任务定义以及目标

### 定义：利用信息技术对与人类医疗健康相关的数据进行处理，挖掘蕴含在这些数据中的有用信息和规律，以服务于医学研究、临床诊疗、公共卫生决策、个人健康咨询等各个领域。

### 目标：针对不同类型的医疗健康相关数据，建立有效的信息抽取和利用的方法、模型和系统，充分挖掘数据潜力，弥补优质医疗资源严重短缺、大大降低误诊率，为实现智能化医疗、提高人类医疗健康服务水平提供必要支撑

## 研究内容和关键科学问题

### 数据通常以以下五种形式存在：1）结构化数据（如检验检查记录）；2）文本（如入院记录、出院记录、病程记录、医学文献等）；3）图形（如心电图、脑电图等）；4）图像（如超声图像、核磁共振图像等）；5）新媒体数据，如微博、微信等

### 在医疗大数据时代，研究工作的研究工作的重心逐渐转移到对于大规模非结构化医疗文本信息的处理，以及将文本信息与结构化信息、图形图像信息的联合处理上来

### 医疗知识图谱构建

- 建立起各种知识之间的关联，涉及到的关键技术包括医疗实体识别以及基于多模态特征的实体链接。
- 在医疗文本中的用语习惯也和我们的日常用语习惯差异巨大，这使得我们针对通用的文本信息处理任务所构建的大量标注数据库难有用武之地，而直接从医疗领域获得的各种类型的加工数据的规模远比通用领域要少

### 辅助诊疗技术研究

- 为了能够进行自动的推理和判断，首先要解决的关键问题是从大量的诊疗实例中进行学习总结的技术与能力，这也是当前医疗文本信息处理所做的最重要的工作之一
- 建立包含文本、图形、图像、检验数据等多模态特征的知识推理能力

### 基于大数据的流行病学研究

- 关键问题1:发现并充分利用能够尽可能提前预测到特定流行病爆发前兆的新的因素，尤其对能够反映与健康相关的群体关注点变化、能够分析社会效应的社交媒体等渠道的分析利用
- 关键问题2:丰富和完善多模态大数据融合分析的模型和技术，从而能够充分结合社交媒体大数据、医疗监测大数据、环境气候大数据等多种因素来联合进行流行性疾病的分布和发展的分析预测

## 技术方法和研究现状

### 医疗实体识别

- 挑战：大量蕴含于临床记录中的有用信息无法被依赖于结构化数据的电子化的临床系统直接使用
- 能够从原始文本中抽取结构化信息的自然语言处理技术在临床医学领域受到了广泛关注
- 重点：临床医疗实体识别

	- 早期：利用临床医疗专家人工构建的字典或规则来识别临床医疗实体
	- 随着可用的标注临床医疗语料的增多，研究者们开始使用机器学习算法来识别临床医疗实体
	- 非连续临床医疗实体的识别的研究仍需深入研究

### 医疗实体链接

- 实体链接主要解决以下三类问题：1）歧义性：相同实体提及对应多个标准实体概念；2）多样性：一个标准实体概念有多种不同的提及形式；3）缺失性：实体提及对应的实体概念没有在给定的标准知识库中出现
- 在医疗领域，多样性现象最为常见，实体链接的研究重点则集中在解决实体多样性的问题
- 研究工作主要面向英文电子病历，面向中文电子病历的实体标链接研究还不多见

### 医疗文本挖掘技术

- 主要目标是从中抽取并建立起多实体之间的关联
- 医疗实体识别和实体链接，都是医疗文本挖掘的基础支撑技术
- 1）有监督学习关系抽取

	- 通常抽取句子级别之间类标的关联关系，如"Apple CEO Steve Jobs said.." 中抽取出 (SteveJobs, CEO, Apple) 三元组
	- 缺点：生成标注集合的代价很高，并且难以加入新的关系，也无法将其方式简单泛化到其他领域

- 2）半监督关系抽取

	- 采用泛型算法，一开始使用一些初始种子模板，然后从文本中抽取符合这些种子模版的新模板，选取其中的前k 个加入种子模板中重复这一过程

- 3）远监督关系抽取

	- 通过现有的知识库和未标注的文本来生成新的样例，找到未标注文本中的相关实体对的位置并假定这个关系可能被该段文本所表示
	- 典型架构：收集大量在统一语句中共现的实体对，如果这两个实体对之间有关系，那么最简单的假设就是所有这样的句子都能够表示这两个实体之间的关系
	- 典型架构过于粗糙，绝大多数出现在同一句话中的实体对实际上是没有关联的
	- 进一步的改进包括假设包含共现的实体对的句子中至少有一个能够表示该实体对的关系，两个实体之间可以表示多种关系，从而将该问题定义成多实例的多类标分类问题
	- 主要缺点是需要高质量的实体匹配技术来对应正确的实体，关系表达假设也具有局限性，并且难以生成有效的负样本

### 医疗健康知识推理技术

- 主要目标之一是对临床医疗医疗预诊、诊断等提供决策建议和帮助，提升医疗诊断的准确率和效率，降低误诊
- 临床决策支持系统（Clinical Decision Support， CDS）

### 流行病分析技术

- 随着大数据和社交媒体的兴起，人们在新的媒体空间中的活动或者讨论等，也成为了流行病预测的重要分析因素，并在流行病预测中扮演着越来越重要的角色
- 基于大数据的流行病预测方法

	- 网络和社交媒体大数据分析方法：某种流行性疾病的搜索结果在短期内激增，这可能准确预示着此种疾病将会暴发
	- 医疗系统大数据分析方法：收集与所监测的疾病相关的一组临床特征（症状）和相关社会现象的发生频率来获取传统公共卫生监测不能提供的疾病防控信息
	- 环境气候及其他大数据分析方法：环境气候变化可能与不同种类的大范围流性病爆发发之间具有一定的对应关系

## 技术展望及发展趋势

### 大规模标准化医疗健康知识库（或知识图谱）的构建

### 中文临床医疗自然语言处理

### 多模态医疗健康信息融合

### 交互式医疗健康信息处理

