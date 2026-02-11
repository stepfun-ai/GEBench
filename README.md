# GEBench: Benchmarking Image Generation Models as GUI Environments

<div align="center">

[![Paper](https://img.shields.io/badge/Paper-arXiv-red)](https://arxiv.org/pdf/2602.09007)
[![Project Page](https://img.shields.io/badge/Project-Page-blue)](YOUR_PROJECT_PAGE_URL)
[![Dataset](https://img.shields.io/badge/Dataset-HuggingFace-green)](https://huggingface.co/datasets/stepfun-ai/GEBench)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Task: GUI Generation](https://img.shields.io/badge/Task-GUI%20Generation-1E90FF)

</div>

![Benchmark Comparison](./assets/teaser.jpg)

## Features

- **5 Data Types**: Type 1 (single-step), Type 2 (multi-step), Type 3 (text-fictionalapp), Type 4 (text-realapp), Type 5 (grounding)
- **Bilingual Support**: Automatic Chinese/English prompt selection based on folder naming
- **5-Dimensional Metrics**: goal, logic, consistency, ui, quality

## Quick Start

### Installation

```bash
# Clone repository
git clone https://github.com/stepfun-ai/GEBench
cd GEBench

# Create conda environment
conda create -n gebench python=3.10 -y
conda activate gebench

# Install dependencies
pip install -r requirements.txt
```
### Data

The GEBench data is available on HuggingFace:

📊 **[StepFun-ai/GEBench](https://huggingface.co/datasets/stepfun-ai/GEBench)** - HuggingFace Datasets Hub

To download:

```bash
cd /path/to/GEBench
git clone https://huggingface.co/datasets/stepfun-ai/GEBench ./data
```

### Generate Images

```bash
python scripts/generate.py --data-type type1 --data-folder data/01_single_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type2 --data-folder data/02_multi_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type3 --data-folder data/03_trajectory_text_fictionalapp --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type4 --data-folder data/04_trajectory_text_realapp --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type5 --data-folder data/05_grounding_data --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY

# With multiple workers
python scripts/generate.py --data-type type1 --data-folder data/01_single_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY --workers 4
```

### Evaluate Results

```bash
python scripts/evaluate.py --data-type type1 --output-folder outputs/gemini/01_single_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type2 --output-folder outputs/gemini/02_multi_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type3 --output-folder outputs/gemini/03_trajectory_text_fictionalapp --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type4 --output-folder outputs/gemini/04_trajectory_text_realapp --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type5 --output-folder outputs/gemini/05_grounding_data --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY

# With multiple workers
python scripts/evaluate.py --data-type type1 --output-folder outputs/gemini/01_single_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
python scripts/evaluate.py --data-type type2 --output-folder outputs/gemini/02_multi_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
python scripts/evaluate.py --data-type type3 --output-folder outputs/gemini/03_trajectory_text_fictionalapp --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
python scripts/evaluate.py --data-type type4 --output-folder outputs/gemini/04_trajectory_text_realapp --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
python scripts/evaluate.py --data-type type5 --output-folder outputs/gemini/05_grounding_data --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
```

## Main Results

### Chinese Subset Results

<table>
<tr style="background-color: #f0f0f0;">
  <th>Model</th>
  <th>Single-Step</th>
  <th>Multi-Step</th>
  <th>Fiction-App</th>
  <th>Real-App</th>
  <th>Grounding</th>
  <th>GE Score</th>
</tr>
<tr>
  <td><strong>Nano Banana pro</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>84.50</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>68.65</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>65.75</strong></td>
  <td style="background-color: #F5DEB3;">64.35</td>
  <td style="background-color: #FFB81C; color: black;"><strong>64.83</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>69.62</strong></td>
</tr>
<tr>
  <td>Nano Banana</td>
  <td>64.36</td>
  <td>34.16</td>
  <td style="background-color: #F5DEB3;">64.82</td>
  <td style="background-color: #FFB81C; color: black;"><strong>65.89</strong></td>
  <td>54.48</td>
  <td>56.74</td>
</tr>
<tr>
  <td><strong>GPT-image-1.5</strong></td>
  <td style="background-color: #F5DEB3;">83.79</td>
  <td style="background-color: #F5DEB3;">56.97</td>
  <td>60.11</td>
  <td>55.65</td>
  <td>53.33</td>
  <td style="background-color: #F5DEB3;">63.22</td>
</tr>
<tr>
  <td>GPT-image-1.0</td>
  <td>64.72</td>
  <td>49.20</td>
  <td>57.31</td>
  <td>59.04</td>
  <td>31.68</td>
  <td>52.39</td>
</tr>
<tr>
  <td>Seedream 4.5</td>
  <td>63.64</td>
  <td>53.11</td>
  <td>56.48</td>
  <td>53.44</td>
  <td>52.90</td>
  <td>55.91</td>
</tr>
<tr>
  <td>Seedream 4.0</td>
  <td>62.04</td>
  <td>48.64</td>
  <td>49.28</td>
  <td>50.93</td>
  <td>53.53</td>
  <td>52.88</td>
</tr>
<tr>
  <td>Wan 2.6</td>
  <td>64.20</td>
  <td>50.11</td>
  <td>52.72</td>
  <td>50.40</td>
  <td style="background-color: #F5DEB3;">59.58</td>
  <td>55.40</td>
</tr>
<tr>
  <td>Flux-2-pro</td>
  <td>68.83</td>
  <td>55.07</td>
  <td>58.13</td>
  <td>55.41</td>
  <td>50.24</td>
  <td>57.54</td>
</tr>
<tr>
  <td>Bagel</td>
  <td>34.84</td>
  <td>13.45</td>
  <td>27.36</td>
  <td>33.52</td>
  <td>35.10</td>
  <td>28.85</td>
</tr>
<tr>
  <td>UniWorld-V2</td>
  <td>55.33</td>
  <td>24.95</td>
  <td>32.03</td>
  <td>21.39</td>
  <td>49.60</td>
  <td>36.66</td>
</tr>
<tr>
  <td>Qwen-Image-Edit</td>
  <td>41.12</td>
  <td>26.79</td>
  <td>23.78</td>
  <td>26.10</td>
  <td>50.80</td>
  <td>33.72</td>
</tr>
<tr>
  <td>Longcat-Image</td>
  <td>48.76</td>
  <td>12.75</td>
  <td>30.03</td>
  <td>30.00</td>
  <td>51.02</td>
  <td>34.51</td>
</tr>
</table>

### English Subset Results

<table>
<tr style="background-color: #f0f0f0;">
  <th>Model</th>
  <th>Single-Step</th>
  <th>Multi-Step</th>
  <th>Fiction-App</th>
  <th>Real-App</th>
  <th>Grounding</th>
  <th>GE Score</th>
</tr>
<tr>
  <td><strong>Nano Banana pro</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>84.32</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>69.51</strong></td>
  <td>46.33</td>
  <td>47.20</td>
  <td style="background-color: #FFB81C; color: black;"><strong>58.64</strong></td>
  <td style="background-color: #F5DEB3;">61.20</td>
</tr>
<tr>
  <td>Nano Banana</td>
  <td>64.80</td>
  <td>50.75</td>
  <td>48.88</td>
  <td>47.12</td>
  <td>49.04</td>
  <td>52.12</td>
</tr>
<tr>
  <td><strong>GPT-image-1.5</strong></td>
  <td style="background-color: #F5DEB3;">80.80</td>
  <td>58.87</td>
  <td style="background-color: #FFB81C; color: black;"><strong>63.68</strong></td>
  <td style="background-color: #FFB81C; color: black;"><strong>58.93</strong></td>
  <td>49.23</td>
  <td style="background-color: #FFB81C; color: black;"><strong>63.16</strong></td>
</tr>
<tr>
  <td>GPT-image-1.0</td>
  <td>60.92</td>
  <td style="background-color: #F5DEB3;">64.33</td>
  <td style="background-color: #F5DEB3;">58.94</td>
  <td style="background-color: #F5DEB3;">56.16</td>
  <td>37.84</td>
  <td>55.64</td>
</tr>
<tr>
  <td>Seedream 4.5</td>
  <td>49.49</td>
  <td>45.30</td>
  <td>53.81</td>
  <td>51.80</td>
  <td>49.63</td>
  <td>50.01</td>
</tr>
<tr>
  <td>Seedream 4.0</td>
  <td>53.28</td>
  <td>37.57</td>
  <td>47.92</td>
  <td>49.36</td>
  <td>44.17</td>
  <td>46.46</td>
</tr>
<tr>
  <td>Wan 2.6</td>
  <td>60.17</td>
  <td>44.36</td>
  <td>49.55</td>
  <td>44.80</td>
  <td>53.36</td>
  <td>50.45</td>
</tr>
<tr>
  <td>Flux-2-pro</td>
  <td>61.00</td>
  <td>52.17</td>
  <td>49.92</td>
  <td>47.16</td>
  <td>45.67</td>
  <td>51.18</td>
</tr>
<tr>
  <td>Bagel</td>
  <td>32.91</td>
  <td>8.61</td>
  <td>26.08</td>
  <td>35.12</td>
  <td>37.30</td>
  <td>28.00</td>
</tr>
<tr>
  <td>UniWorld-V2</td>
  <td>42.68</td>
  <td>14.14</td>
  <td>30.08</td>
  <td>26.83</td>
  <td>47.04</td>
  <td>32.15</td>
</tr>
<tr>
  <td>Qwen-Image-Edit</td>
  <td>40.12</td>
  <td>18.61</td>
  <td>25.80</td>
  <td>25.95</td>
  <td style="background-color: #F5DEB3;">54.55</td>
  <td>33.01</td>
</tr>
<tr>
  <td>Longcat-Image</td>
  <td>36.69</td>
  <td>8.44</td>
  <td>37.30</td>
  <td>36.83</td>
  <td>47.12</td>
  <td>33.28</td>
</tr>
</table>

**Legend:** <span style="background-color: #FFB81C; padding: 2px 6px;">Orange (🥇 Top 1)</span> and <span style="background-color: #F5DEB3; padding: 2px 6px;">Champagne (🥈 Top 2)</span> indicate the best performers.

## Citation

If you find GEBench useful, please cite our paper:

```bibtex
@article{li2026gebench,
  title={GEBench: Benchmarking Image Generation Models as GUI Environments},
  author={Haodong Li and Jingwei Wu and Quan Sun and Guopeng Li and Juanxi Tian and Huanyu Zhang and Yanlin Lai and Ruichuan An and Hongbo Peng and Yuhong Dai and Chenxi Li and Chunmei Qing and Jia Wang and Ziyang Meng and Zheng Ge and Xiangyu Zhang and Daxin Jiang},
  journal={arXiv preprint arXiv:2602.09007},
  year={2026}
}
```
