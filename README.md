# Stable Diffusion Demo 🤖 🖼️
This repo contains info, configs, and notes for running stable diffusion locally.

## Enviroment
### Hardware 
- GPU: Nvidia GeForce RTX3070 (Laptop) (8GB GDDR6 VRAM)
- RAM: 32GB DDR4

### Software
- OS: Win 11
- Python 3.10.0
- Model Checkpoint: v1-4

## Installation Steps
1. Download weights [^1]
2. Download any fork, I used the web-ui fork [^2]
3. Change to `name: ldo` in environment.yaml
4. Rename weights `.ckpt` file to `model.ckpt` and place in `/models/ldm/stable-diffusion-v1` directory
5. Run `conda env create -f environment.yaml` in (base) miniconda3
6. Activate env by `conda activate ldo`
7. Run `webui.cmd` in (ldo)

**NOTE**: The original repo [^3] gave me a `RuntimeError: CUDA Out Of Memory` even with `--n_samples 1`. The optimized fork [^4] has all the safety_checks removed and uses less VRAM and has a faster result generation time.

P.S. _I didn't try the `model.half()` tip that some people have suggested to use with the original repo for low VRAM usage._

## Results (cherrypicked ofc!)

<div>
<code>Prompt#1: "a cat wearing a red hat"</code>
</div>
<br>
<span>
<img src="https://i.imgur.com/bVWWMWN.png" width="200">
<img src="https://i.imgur.com/mE4mZuR.png" width="200">
<img src="https://i.imgur.com/4NuyDzR.png" width="200">
<img src="https://i.imgur.com/3wghOrX.png" width="200">
</span>
<br><br>
<div>
<code>Prompt#2: "a busy indian street market, artstation digital art"</code>
</div>
<br>
<span>
<img src="https://i.imgur.com/XuAcU60.png" width="200">
<img src="https://i.imgur.com/ZuCJjKW.png" width="200">
<img src="https://i.imgur.com/mQt1EAh.png" width="200">
<img src="https://i.imgur.com/yY2UIzz.png" width="200">
</span>
<br><br>
<div>
<code>Prompt#3: "a rat in a shiny medieval armour posing for a victorian era portrait, oil painting"</code>
</div>
<br>
<span>
<img src="https://i.imgur.com/y9GD8MN.png" width="200">
<img src="https://i.imgur.com/ITIzYTF.png" width="200">
<img src="https://i.imgur.com/fiT5zZU.png" width="200">
<img src="https://i.imgur.com/TyKEkhn.png" width="200">
</span>
<br><br>
<div>
<code>Prompt#4: "a steampunk flying machine flying in a beautiful blue sky, 4k"</code>
</div>
<br>
<span>
<img src="https://i.imgur.com/S2555TC.png" width="200">
<img src="https://i.imgur.com/TrFqnsS.png" width="200">
<img src="https://i.imgur.com/jn7Gan3.png" width="200">
<img src="https://i.imgur.com/4NmXpv5.png" width="200">
</span>
<br>

## Stats
I generated images in batches of 4 at a time.

Generation time ~ 40s (10s per image)

Peak memory usage: 7854 MiB / 8192 MiB / 95.871%

The cyberpunk one (Prompt#4) was an outlier, it took 330.05s total (82.51s per image).

## References
[^1]: https://huggingface.co/CompVis
[^3]: https://github.com/CompVis/stable-diffusion 
[^4]: Optimized: https://github.com/basujindal/stable-diffusion (Worked well enough)
[^2]:WebUI with all optimizations pre-applied: https://github.com/sd-webui/stable-diffusion-webui
[^5]: model.half() text2img only tip: https://www.reddit.com/r/StableDiffusion/comments/wuyu2u/comment/ilgr0lu/ (NOT TESTED)
