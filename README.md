# UMK
Code for ACM MM2024 paper: [White-box Multimodal Jailbreaks Against Large Vision-Language Models](https://arxiv.org/abs/2405.17894)


![image](https://github.com/roywang021/UMK/model.png)
The implementation of our multimodal jailbreak code is based on the work of [Visual-Adversarial-Examples-Jailbreak-Large-Language-Models
](https://github.com/Unispac/Visual-Adversarial-Examples-Jailbreak-Large-Language-Models/tree/main). Gratitude is extended to the original authors for their valuable contributions and commitment to open source.

### Basic Setup
The fundamental setup tasks (e.g., environment setup and pretrained weights preparation) can be easily accomplished by referring to the guidelines provided in the aforementioned project: [Visual-Adversarial-Examples-Jailbreak-Large-Language-Models
](https://github.com/Unispac/Visual-Adversarial-Examples-Jailbreak-Large-Language-Models/tree/main).

### Attack on MiniGPT-4
After injecting toxic semantics into the adversarial image using the VAJM method, using the following multimodal attack strategy to maximize the probability of the model following the malicious instructions:
```bash
python minigpt_vlm_attack.py --cfg-path eval_configs/minigpt4_eval.yaml  --gpu-id 0 --n_iters 5000  --alpha 1 --save_dir vlm_unconstrained
```

### Evaluation
We provide code for evaluation on two different datasets:

#### Evaluation on VAJM test set

```bash
python minigpt_test_manual_prompts_vlm.py --cfg-path eval_configs/minigpt4_eval.yaml  --gpu-id 0 --image_path  vlm_unconstrained/bad_prompt.bmp
```
#### Evaluation on Advbench
```bash
python minigpt_test_advbench.py --cfg-path eval_configs/minigpt4_eval.yaml  --gpu-id 0 --image_path  vlm_unconstrained/bad_prompt.bmp
```

