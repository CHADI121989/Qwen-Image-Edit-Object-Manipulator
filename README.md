# **Qwen-Image-Edit-Object-Manipulator**

> A Gradio-based demonstration for the Qwen/Qwen-Image-Edit-2511 model, specialized in object manipulation via lazy-loaded LoRA adapters. Supports adding or removing specific elements (e.g., logos, accessories, clothing) in single- or multi-image inputs while preserving lighting, realism, and background details. Features precise prompt control and fast inference with Flash Attention 3.

## Features

- **Object Addition/Removal**: Add elements (e.g., "Add batman logo") or remove (e.g., "Remove necklace") with natural integration.
- **Multi-Image Support**: Upload gallery for reference-based edits (e.g., transfer pose or style).
- **Lazy LoRA Loading**: 2 adapters (Object-Adder, Object-Remover) load on-demand to optimize memory.
- **Rapid Inference**: 4-step default generations with bfloat16 and Flash Attention 3.
- **Auto-Resizing**: Maintains aspect ratio up to 1024px max edge (multiples of 8).
- **Custom Theme**: OrangeRedTheme with responsive layout.
- **Examples**: 4 curated scenarios for quick testing.
- **Queueing**: Up to 30 concurrent jobs.

---

<img width="4200" height="2625" alt="SQp9XAlYp7N08VAWg9KnH" src="https://github.com/user-attachments/assets/3ed07862-586f-40cd-a3d6-56e827744b29" />
<img width="1800" height="1125" alt="p2ezcG3uN1a0WjcO2VusT" src="https://github.com/user-attachments/assets/a9771750-6c46-4811-b514-fcf715278254" />
<img width="4200" height="2625" alt="ILqeYxJg3wjh28bnpmUTK" src="https://github.com/user-attachments/assets/d893ece3-8038-45f5-9e7a-3dc5f79151f0" />
<img width="1800" height="1125" alt="ECUOiU7HLnir26iIjCPoY" src="https://github.com/user-attachments/assets/7c053db8-1988-4f17-88af-fd55c6407340" />
<img width="4200" height="2625" alt="AqwrsNO-RDSF2OxZG06kx" src="https://github.com/user-attachments/assets/1b8bca50-1ff0-4695-8b96-a7beccc32081" />
<img width="1800" height="1125" alt="_EcUfxwqvRIom-_QbQTVC" src="https://github.com/user-attachments/assets/3cfc2903-a407-4c11-873d-a2766167f679" />

---

**Note**: Experimental for Qwen-Image-Edit-2511; consider [2509 version](https://huggingface.co/spaces/prithivMLmods/Qwen-Image-Edit-2509-LoRAs-Fast) for stability.

## Prerequisites

- Python 3.10 or higher.
- CUDA-compatible GPU (required for bfloat16 and Flash Attention 3).
- pip >= 23.0.0 (see pre-requirements.txt).
- Stable internet for initial model/LoRA downloads.

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/PRITHIVSAKTHIUR/Qwen-Image-Edit-Object-Manipulator.git
   cd Qwen-Image-Edit-Object-Manipulator
   ```

2. Install pre-requirements:
   Create a `pre-requirements.txt` file with the following content, then run:
   ```
   pip install -r pre-requirements.txt
   ```

   **pre-requirements.txt content:**
   ```
   pip>=23.0.0
   ```

3. Install dependencies:
   Create a `requirements.txt` file with the following content, then run:
   ```
   pip install -r requirements.txt
   ```

   **requirements.txt content:**
   ```
   git+https://github.com/huggingface/transformers.git@v4.57.3
   git+https://github.com/huggingface/accelerate.git
   git+https://github.com/huggingface/diffusers.git
   git+https://github.com/huggingface/peft.git
   huggingface_hub
   sentencepiece
   torchvision
   supervision
   kernels
   spaces
   gradio
   hf_xet
   torch
   numpy
   av
   ```

4. Start the application:
   ```
   python app.py
   ```
   The demo launches at `http://localhost:7860`.

## Usage

1. **Upload Images**: Use gallery for one or more images (e.g., base + reference).

2. **Select Manipulator**: Choose "Object-Adder" or "Object-Remover".

3. **Enter Prompt**: Describe the action (e.g., "Add the batman logo while preserving background lighting").

4. **Configure (Optional)**: Expand "Advanced Settings" for seed, guidance, steps.

5. **Edit Image**: Click "Edit Image" to generate output.

### Supported Manipulators

| Manipulator         | Use Case                                      |
|---------------------|-----------------------------------------------|
| Object-Adder       | Add elements (logos, accessories) realistically |
| Object-Remover     | Remove items (jewelry, goggles) seamlessly    |

## Examples

| Input Images     | Prompt Example                                                                 | Manipulator          |
|------------------|-------------------------------------------------------------------------------|----------------------|
| examples/D.jpg  | "Add the batman logo to the image while preserving background lighting and details." | Object-Adder        |
| examples/A.jpg  | "Add slim rectangular transparent frame sunglasses while preserving lighting." | Object-Adder        |
| examples/B.jpeg | "Remove the necklace and goggles while preserving background and details."    | Object-Remover      |
| examples/C.png  | "Add the leather cowboy cap while preserving lighting and surroundings."      | Object-Adder        |

## Troubleshooting

- **Manipulator Loading**: First use downloads LoRA; check console.
- **OOM**: Reduce steps/resolution; clear cache with `torch.cuda.empty_cache()`.
- **Flash Attention Fails**: Fallback to default; requires compatible CUDA.
- **Gallery Input**: Supports filepaths, tuples, or PIL objects.
- **No Output**: Ensure image uploaded and prompt specific.

## Contributing

Contributions welcome! Add new manipulators to `ADAPTER_SPECS`, improve prompts, or enhance multi-image support.

Repository: [https://github.com/PRITHIVSAKTHIUR/Qwen-Image-Edit-Object-Manipulator.git](https://github.com/PRITHIVSAKTHIUR/Qwen-Image-Edit-Object-Manipulator.git)


## License

Apache License 2.0. See [LICENSE](LICENSE) for details.

Built by Prithiv Sakthi. Report issues via the repository.
