<div align=center>
  <img width=400 src="https://github.com/yangbisheng2009/nsfw-resnet/blob/master/image/nsfw_logo.jpg" >
</div>

English | [中文版](https://github.com/yangbisheng2009/nsfw-resnet/blob/master/README_cn.md)  

# NSFW
NSFW - not safe for work

![Python 3.7](https://img.shields.io/badge/python-3.7-green.svg?style=plastic)
![Pytorch 1.4.0](https://img.shields.io/badge/pytorch-1.4.0-green.svg?style=plastic)
![cuDNN 7.3.1](https://img.shields.io/badge/cudnn-7.3.1-green.svg?style=plastic)
![License CC BY-NC](https://img.shields.io/badge/license-CC_BY--NC-green.svg?style=plastic)

## Description
Trained on 600,000 labled pictures:  

- `porn` - pornography images
- `hentai` - hentai images, but also includes pornographic drawings
- `sexy` - sexually explicit images, but not pornography. Think nude photos, playboy, bikini, etc.
- `neutral` - safe for work neutral images of everyday things and people
- `drawings` - safe for work drawings (including anime)

## Requeriments
pytorch 1.0+  
If you want pytorch 0.4, please download V1 release.  

## Usage
```shell
#train
python train.py --model resnet101 --epochs 90 --batch-size 512 --checkpoint ./checkpoint --data-dir ./data

#test
python test_confusion_matrix.py

#predict
python predict --model resnet101 --checkpoint ./checkpoint/x

#if your machine has connected to the internet and you dosen't want to download the image to your disk
cat urls.txt | python predict_url.py
```

## Training data source
Special thanks to the [nsfw_data_scraper](https://github.com/alexkimxyz/nsfw_data_scrapper) for the training data.  If you're interested in a more detailed analysis of types of NSFW images, you could probably use this repo code with [this data](https://github.com/EBazarov/nsfw_data_source_urls).  
If you want make better result.Contact [me](https://twitter.com/yangbisheng2009).I can provide you the best training data.  

## Current status
<div align=left>
  <img width=700 src="https://github.com/yangbisheng2009/nsfw-resnet/blob/master/image/test_confusion_matrix.jpg" >
</div>

Sexy and porn is a little similar.In my view,it does'nt matter.
&emsp;  
&emsp;  

**SEXY**
<div align=left>
  <img width=200 height=250 src="https://github.com/yangbisheng2009/nsfw-resnet/blob/master/image/sexy_demo.jpg" >
</div>
&emsp;  
&emsp;  

**NETURAL**
<div align=left>
  <img width=200 height=250 src="https://github.com/yangbisheng2009/nsfw-resnet/blob/master/image/netural_demo.jpg" >
</div>

## Detail
I have tried various methods include some pretrained models like resnet/inceptionv3 and data augumentation and finetuing.

Here are some tips which make a greate effect to the final result:

- Make batch size bigger.(the bigger the better since I make it 512 with my p40)
- Use pretrained model.(you can use torchvision. pretrained model can help your model convergence more faster)
- Lock some layer and finetune FC.(after train_init.py then lock some layer just finetune the FC)
- Adjust learning rate.(make lr dynamic when training in order to get saddle point)
- Select appropriate pretrained model.(I choose resnet101 since it receive better result than resnet50 or inceptionv3)

## Thanks
Thanks for my wife FeiFei Li. She gave me lots of encouragement. And made the beautiful logo for NSFW preject.  
Thanks for my workmate Kuai Li. He gave me lots of good suggestion.  

## Join us
If you have good points.Join us!

## References
https://github.com/GantMan/nsfw_model  
