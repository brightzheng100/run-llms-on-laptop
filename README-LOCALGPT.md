# Run LLM models with locally ingested documents with `localGPT`

As per the [localGPT](https://github.com/PromtEngineer/localGPT)'s doc:

```
LocalGPT is an open-source initiative that allows you to converse with your documents without compromising your privacy. With everything running locally, you can be assured that no data ever leaves your computer. Dive into the world of secure, local document interactions with LocalGPT.
```

## The TL'DR Setup Guide

```sh
# Use conda to create a new Python env
conda create -n localgpt python=3.11
conda activate localgpt

# Clone and project
git clone https://github.com/PromtEngineer/localGPT.git
cd localGPT

# Install the Python packages
pip install -r requirements.txt
CMAKE_ARGS="-DLLAMA_METAL=on"  FORCE_CMAKE=1 pip install llama-cpp-python==0.1.83 --no-cache-dir

# There is one Orca paper namely "Orca: Progressive Learning from Complex Explanation Traces of GPT-4"
# under the folder of "SOURCE_DOCUMENTS".
# And you can add your docs for the model to learn too.
# For example, let's add the "" doc:
wget https://constitutioncenter.org/media/files/constitution.pdf -O "./SOURCE_DOCUMENTS/ConstitutionOfUSA.pdf"

# Ingest the docs
python ingest.py --device_type mps

# Now start the server and play with it
python run_localGPT.py --device_type mps
```

The default LLM model enabled is [`TheBloke/Llama-2-7b-Chat-GGUF`](https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGUF) with filename of `llama-2-7b-chat.Q4_K_M.gguf`.
You can try other LLM models by updating the `constants.py` file.

## Play with it

Since the LLM model has learnt some very specific docs, on top of the generic big data training, you may try asking some interesting questions, like:
- What's the term of the US President?
- How does Progressive Learning from Complex Explanation Traces of GPT-4 work?
- Tell me a joke
- Write a Java application where it has a sum method which can be used to calculate the sum of two integers.

And here is a very quick GIF recording:
![localGPT screenshots](./screenshots/localgpt.gif)

PS: I didn't see much performance impact in my MacBook Pro while playing with it.
