# Select and Transfer

**Select and Transfer: Selective Cross-Modal Relational Transfer for Domain Generalization in Vision-Language Models**

Qin Xu, Hongtao Lu, Bo Jiang, and Bin Luo · Anhui University

## Method

Select and Transfer adapts a pretrained CLIP model to labeled source data while preserving cross-modal relations that help it generalize to unseen domains.

1. **Informative relation selection.** With both pretrained encoders frozen, the Agent-Guided Relation Module (AGRM) builds class-wise relation embeddings from local visual tokens and multiple text descriptions per class. A shared scorer and an information bottleneck objective jointly encourage predictive sufficiency and redundancy compression.
2. **Relational knowledge transfer.** The selected AGRM is frozen. It maps teacher and student tokens into a shared relation space. The student adapts using source classification and an alignment loss that matches the teacher's class-centered relational geometry.

At inference, the adapted visual encoder and cached text prototypes form the classifier. The teacher and AGRM are discarded.

## Benchmarks and manuscript results

| Setting | Protocol | Reported result |
| --- | --- | --- |
| Domain generalization | Leave-one-domain-out on PACS, VLCS, OfficeHome, TerraIncognita, and DomainNet | 81.29% mean accuracy |
| ImageNet distribution shifts | Adapt on ImageNet-1K and evaluate on ImageNet-V2, ImageNet-Sketch, ImageNet-A, and ImageNet-R | 61.95% mean shifted accuracy |
| Base-to-novel recognition | 16-shot adaptation on base classes across 11 datasets, followed by separate base and novel evaluation | 85.12% base accuracy, 77.28% novel accuracy, and 81.01% harmonic mean |

Use the [DomainBed dataset instructions](https://github.com/facebookresearch/DomainBed) for the five domain generalization datasets and the [CoOp dataset guide](https://github.com/KaiyangZhou/CoOp/blob/main/DATASETS.md) for the ImageNet variants and base-to-novel datasets.

## Citation

```bibtex
@unpublished{xu2026selectandtransfer,
  title  = {Select and Transfer: Selective Cross-Modal Relational Transfer
            for Domain Generalization in Vision-Language Models},
  author = {Xu, Qin and Lu, Hongtao and Jiang, Bo and Luo, Bin},
  year   = {2026},
  note   = {Manuscript}
}
```

For correspondence about the manuscript, contact Qin Xu at [xuqin@ahu.edu.cn](mailto:xuqin@ahu.edu.cn).

## Acknowledgments

This project builds on [CLIP](https://github.com/openai/CLIP), [CLIPood](https://github.com/thuml/CLIPood), [Transfer-Learning-Library](https://github.com/thuml/Transfer-Learning-Library), [DomainBed](https://github.com/facebookresearch/DomainBed), and [CoOp](https://github.com/KaiyangZhou/CoOp). See [LICENSE](LICENSE) for licensing information.
