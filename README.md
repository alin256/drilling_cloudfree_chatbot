# Cloud-Free Question Answering Chatbot for Drilling Applications
The supporting code for [the paper "Cloud-Free Question Answering from Internal Knowledge Bases: Building an AI for Drilling Applications"](#cite-as) developed by 
[Liang Zhang](https://github.com/zl6977), 
Felix James Pacis, 
[Sergey Alyaev](https://github.com/alin256). 


## Installation

### 1. Install Ollama

Install an appropriate ollama version using the download instructions: https://ollama.com/download

For linux without admin rights, you can extract the ollama from one of [the pre-compiled releases](https://github.com/ollama/ollama/releases). In our testing, we used the [AMD64 NVIDIA version 0.5.4](https://github.com/ollama/ollama/releases/download/v0.5.4/ollama-linux-amd64.tgz).

### 2. Download and run an open LLM

Download an LLM for summarization and run it as a service locally.

For llama3.1:8b - small model (--model small), run:

```
ollama run llama3.1:8b
```

For llama3.3 - large model (requires 32+ GB RAM memory) (--model default), run:

```
ollama run llama3.3
```

Keep the service running in the background.

### 3. Install Git Large File Storage (LFS) to download large weights file

Install Git LFS following [the instructions](https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage).

For Ubuntu linux:

```
apt-get install git-lfs
git lfs install
```

Or, if you do not want to install git-lfs, you can download the weights file `ft_models_v2/6config/model.safetensors` manually and put it in the right place.

### 4. Download this code

```
git clone https://github.com/NORCE-DrillingAndWells/drilling_cloudfree_chatbot.git
```

Ensure the weights file `ft_models_v2/6config/model.safetensors` is the right one.
It can be just a placeholder if you download the code using `git clone` without installing `git-lfs`.
In this case, download the right file manually.

### 5. Create and activate a virtual enviornment

If necessary, you can create an isolated virtual enviornment to avoid corrupting the versions of dependencies in your global environment.

Create a virtual enviornment:

```
python -m venv chatbotvenv
```

To activate the virtual enviornment:

- on Windows:

```
chatbotvenv\Scripts\activate.bat
```

- on Linux and MacOS:

```
source chatbotvenv/bin/activate
```

### 6. Install setuptools

```
pip install setuptools
```

### 7. Install dependencies from setup.py

```
cd src
pip install .
```

## Usage

### Ensure the LLM is running

The chatbot communicates with a locally deployed LLM.
If set up correctly, there should be an LLM server on `http://localhost:11434` (the default port used by ollama).
To check the running model, run `ollama ps`.
To start the server, for example, run `ollama run llama3.1:8b`.

### Run the chatbot

For the chatbot with small model

```
python src/chatbot_demo.py chatbot --model small
```

For testing with default model

```
python src/chatbot_demo.py test --model default
```

## Examples from the paper
The [results](results) folder contains the answers produced by the Offline Chatbot as reported in the paper, see [Cite as](#cite-as).

## Cite as

Liang Zhang, Felix James Pacis, Sergey Alyaev, Tomasz Wiktorski. **"Cloud-Free Question Answering from Internal Knowledge Bases: Building an AI for Drilling Applications."** First Break 43, no. 2, 2025. [URL: https://www.earthdoc.org/content/journals/10.3997/1365-2397.fb2025012](https://www.earthdoc.org/content/journals/10.3997/1365-2397.fb2025012)

### Latex

```
@article{zhang2025cloudfree,
  title={Cloud-Free Question Answering from Internal Knowledge Bases: Building an AI for Drilling Applications},
  author={Zhang, Liang and Pacis, Felix James and Alyaev, Sergey and Wiktorski, Tomasz},
  journal={First Break},
  volume={43},
  number={2},
  year={2025},
  publisher={European Association of Geoscientists \& Engineers},
  url={https://www.earthdoc.org/content/journals/10.3997/1365-2397.fb2025012}
}
```

### For citing the code

[Liang Zhang](https://github.com/zl6977), 
Felix James Pacis, 
[Sergey Alyaev](https://github.com/alin256) (2025). 
**Cloud-Free Question Answering Chatbot for Drilling Applications**, Zenodo.
[![DOI](https://zenodo.org/badge/911206641.svg)](https://doi.org/10.5281/zenodo.14794898)

## Licences
#### License

- This code is distributed under the [open-source license which requires citing this work](LICENSE).

#### Third party licences:

- The `E5-small-v2` base model is distributed under the [MIT license](https://choosealicense.com/licenses/mit/).
