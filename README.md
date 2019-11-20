# Strongeryolo-pytorch 

## Introduction
This project is inspired by [Stronger-Yolo](https://github.com/Stinky-Tofu/Stronger-yolo). I reimplemented with Pytorch and continue improving yolov3 with latest papers.  
This project will also try out some model-compression approaches(e.g. channel-pruning).  
See **reimplementation results** in [MODELZOO](docs/MODELZOO.md).
## Environment
python3.6, pytorch1.2(1.0+ should be ok), ubuntu14/16/18 tested.

## Quick Start
**See [Usage.md](docs/Usage.md) for details.** 
## Improvement with latest papers(Using StrongerV3 as baseline)
|model|mAP50|mAP75|configs|
| ------ | ------ | ------ |------ |
|baseline(with GIOU)|0.765 |0.391|voc.yaml|
|+ [focal loss](https://arxiv.org/abs/1708.02002)|0.772|0.438 |strongerv3_clsfocal.yaml|
|+ [kl loss](https://github.com/yihui-he/KL-Loss)|0.778|0.449 |strongerv3_kl.yaml|
|+ [var vote](https://github.com/yihui-he/KL-Loss)|0.781|0.464 |strongerv3_kl.yaml|

Note:  
1.Set EVAL.varvote=True to enable varvote in KL-loss. 

## Performance on VOC2007 Test(mAP) after pruning
|Model| MAP | Flops(G)| Params(M)|
| ------ | ------ | ------ | ------ |
strongerv3| 79.6|4.33|6.775|
strongerv3-sparsed|77.4|4.33|6.775|
strongerv3-Pruned(30% pruned) |77.1 |3.14|3.36|

Note:  
1.All experiments are trained for 60 epochs.  
2.All experiments tested with threshold 0.1 in 512 resolution.
## Supported backbone
- [x] MobileV2
- [x] DarkNet  
...
## Reference
[Stronger-Yolo](https://github.com/Stinky-Tofu/Stronger-yolo)  
[focal-loss](https://arxiv.org/abs/1708.02002)  
[kl-loss](https://github.com/yihui-he/KL-Loss)
