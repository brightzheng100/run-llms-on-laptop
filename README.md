# Run LLM Models on Laptop

In general, running AI models demands quite decent amount of resources in terms CPUs, RAM, disks and even expensive GPUs.
So you may be curious: can I run LLM models on my laptop?

Here are my experiments, trying to answer below key questions that I also had before.

By given my current laptop, say MacBook Pro:
- Can I run the LLM models on top of it?
- If yes, what are the potential approaches to run the LLM models locally?

My laptop specs: MacBook Pro, with M1 Max chip, 10 CPU cores, 32G RAM, and 1T SSD disk.

Your miles may vary but you will know how. Let's do it!

## Preparation

Python is the de facto language while running most of the AI models, including LLM ones.
And [Miniconda](https://docs.anaconda.com/free/miniconda/index.html) is one of the best Python package & environment managers that I'd highly recommend, which includes `Python`, `conda` and frequently used packages.

So let's download and install the latest `Miniconda`:

```sh
# Download the installer script
wget "https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-`uname -m`.sh"

# Grant it execution permission and then run it
chmod +x "Miniconda3-latest-MacOSX-`uname -m`.sh"
./"Miniconda3-latest-MacOSX-`uname -m`.sh"
```

Just follow the guide to finish the installation, with some recommendations when being prompted:
- Do you wish to update your shell profile to automatically initialize conda? **Yes**, which will init `conda` for us.

Make sure to source the init before using the `conda`.
In my case, as I'm with `zsh`, do this: `source ~/.zshrc`.

And I personally prefer to disable the auto base activation, so run this:
```sh
conda config --set auto_activate_base false
```

Now, we're all set.

## Approachs

There might be more and more approaches that can be discovered and below are what I've tried.
So check out the experiment link for details.
   
| SN | Approach | Briefing    | Experiment Link |
|----|----------|-------------|-----------------|
| 1  | [localGPT](https://github.com/PromtEngineer/localGPT) | Run LLM models with locally ingested documents  | [README-LOCALGPT.md](README-LOCALGPT.md) |
| 2  | [text-generation-webui](https://github.com/oobabooga/text-generation-webui) | A popular web UI for running Large Language Models | [README-TEXTGEN-WEBUI.md](README-TEXTGEN-WEBUI.md) |
| 3  | [`ollama` CLI](https://ollama.com/) | A CLI to run Llama 2 and other LLMs locally | [README-OLLAMA.md](README-OLLAMA.md) |

> Disclaimers: the sequence ("SN") here is just the sequence that I tried these approaches, which has no indication of anything about ranking or preference.
