### シナプスについて
シナプスの種類はニューロンをConnectするときに設定する。
neuron1とneuron2をつなげる方法は
```
nest.Connect(neuron1,neuron2)
```
デフォルトは"static_synapse"(後シナプス電流の形がα関数で表される).  
一回の発火で発生する **後シナプス電流の最大値は1.0pA.** 
最大値はweightで設定する.  
例えばsynapseの種類をSTP(Short Term Plasticity) (=tsodyks2_synapse), 一回の発火で発生する後シナプス電流の最大値を10pAとしたいとき
```
nest.Connect(neuron1,neuron2,"tsodyks2_synapse")
cons = nest.GetConnections(neuron1,neuron2)
nest.SetStaus(cons,"weight",10.0)
```
または
```
nest.SetDefaults("tsodyks2_synapse",{"weight": 10.0})
nest.Connect(neuron1,neuron2,"tsodyks2_synapse")
```
または
```
nest.Connect(neuron1,neuron2,params={"weight":10.0},model="tsodyks2_synapse"
```
などとすればよい。  
weightはdouble型なので **10** とするのではなく**10.0** や **10.** などとする必要がある.  
その他,電流伝達の遅延（delay)やシナプスの数の設定などが可能.  

詳しくは以下のページを参考に  
http://www.nest-simulator.org/connection-management/  
http://www.nest-simulator.org/part-3-connecting-networks-with-synapses/
