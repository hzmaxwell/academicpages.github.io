---
title: "Wider and Deeper, Cheaper and Faster: Tensorized LSTMs for Sequence Learning. [[PDF](http://papers.nips.cc/paper/6606-wider-and-deeper-cheaper-and-faster-tensorized-lstms-for-sequence-learning)]"
collection: publications
permalink: /publication/tLSTM
citation: '<b>Zhen He</b>, Shaobing Gao, Liang Xiao, Daxue Liu, Hangen He, David Barber.<br/>
In <i>Advances in Neural Information Processing Systems</i> (<b>NIPS 2017</b>), Long Beach, USA.'
---
## Abstract
Long Short-Term Memory (LSTM) is a popular approach to boosting the ability of Recurrent Neural Networks to store longer term temporal information. The capacity of an LSTM network can be increased by widening and adding layers. However, usually the former introduces additional parameters, while the latter increases the runtime. As an alternative we propose the Tensorized LSTM in which the hidden states are represented by tensors and updated via a cross-layer convolution. By increasing the tensor size, the network can be widened efficiently without additional parameters since the parameters are shared across different locations in the tensor; by delaying the output, the network can be deepened implicitly with little additional runtime since deep computations for each timestep are merged into temporal computations of the sequence. Experiments conducted on five challenging sequence learning tasks show the potential of the proposed model.
