**2022/12/13**

|        Title         | MetaFormer Is Actually What You Need for Vision              |
| :------------------: | :----------------------------------------------------------- |
|   **Short Title**    | PoolFormer                                                   |
|    **ArXiv Time**    | 2022.7.4                                                     |
|       **Code**       | https://github.com/sail-sg/poolformer / mmcls                |
|    **Motivation**    | 近来，Vision Transformer 大火，人们普遍认为自注意力机制是ViT性能好的原因；但是，又有相关工作将自注意力机制换替换成 spatial MLP (相对于 channel MLP )，ViT也能表现的很好； 因此，该工作认为是 Transformer 的整体架构使得 ViT 具有良好的性能，而不是某种 token 交互方式。随后，该论文直接使用简单的 average pooling 2D 操作来对 token 进行交互，实验证明 PoolFormer 依然具有较好的性能。 |
|   **Contribution**   | 1. 证明了是 Transformer 的整体架构而不是 MHSA 使得 ViT 性能良好，将这种架构抽象为 MetaFormer； 2. 启发未来工作将重心移到整体架构的改进上，而非改进 token 混合方式，如MHSA； |
|      **Method**      | ![image-20221222211834423](pics/image-20221222211834423.png?lastModify=1671766086?lastModify=1671766086) 整体 block 与 ViT 相同，使用 AvgPooling2D 做 token 交互，随后再使用正常的 channel MLP 对 token 进行非线性映射；整体结构非常简单，代码中 tokens 始终是二维特征图的形式，并没有构成 sequence。 ![image-20221222212330864](pics/image-20221222212330864.png?lastModify=1671766086?lastModify=1671766086) PoolFormer，每个阶段都 Patch embedding 来下采样； |
|     **Results**      | PoolFormer-S36 31 5.0 **81.4**；怎么说呢，那肯定是不如 VAN。 |
| **Compared Methods** | ResNet、ViT、DeiT、PVT-1、Swin-1； ResMLP、MLP-Mixer、g-MLP； |



