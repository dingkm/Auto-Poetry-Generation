# Auto-Poetry-Generation
Automatically Generate Chinese Tradition Poetry By LSTMs using Pytorch
## Dataset
All the data comes from [chinese-poetry](https://github.com/chinese-poetry/chinese-poetry).
It contains traditional poetry about 55k in Tang Dynasty, 260k in Song Dynasty and other genres. Poets including Tang and Song are about 14 thousand.
All the data is from the Internet by scratching. It's our responsibility to inherit all the cultures.
## Usage
All the parameters are in the class Config. We can change these parameters as following.
```
 data_path = 'data/' # 诗歌的文本文件存放路径
    pickle_path= 'tang.npz' # 预处理好的二进制文件 
    author = None # 只学习某位作者的诗歌
    constrain = None # 长度限制
    category = 'poet.tang' # 类别，唐诗还是宋诗歌(poet.song)
    lr = 1e-3 
    weight_decay = 1e-4
    use_gpu = True
    epoch = 20  
    batch_size = 128
    maxlen = 125 # 超过这个长度的之后字被丢弃，小于这个长度的在前面补空格
    plot_every = 20 # 每20个batch 可视化一次
    # use_env = True # 是否使用visodm
    env='poetry' # visdom env
    max_gen_len = 200 # 生成诗歌最长长度
    debug_file='/tmp/debugp'
    model_path=None # 预训练模型路径
    prefix_words = '细雨鱼儿出,微风燕子斜。' # 不是诗歌的组成部分，用来控制生成诗歌的意境
    start_words='闲云潭影日悠悠' # 诗歌开始
    acrostic = False # 是否是藏头诗
    model_prefix = 'checkpoints/tang' # 模型保存路径
```
## Demo
The well-trained weights are in the **checkpoints/tang_199.pth** file.
We can change the **acrostic=True** to decide whether acrostic. And the **prefix_words** is to control the feeling of the whole poetry.
```
para = {'model_path':'checkpoints/tang_199.pth','pickle_path':'data/tang.npz','start_words':'吾父小丁',
         'prefix_words':'亲朋无一字，老病有孤舟。'}
```
We can get generated poetry like 
>>  吾亦生死別，何由问长流。父子已及朝，翩翩準自周。
>> 小壺劝我酒，左右皆具修。丁来视箧笥，为客唯布裘。

Quite interesting example.
Acknowledge Chen Yun, the writer of book  《深度学习框架PyTorch：入门与实战》. Github like is [here.](https://github.com/chenyuntc/pytorch-book)
