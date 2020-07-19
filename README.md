# GPT-3 Sandbox: From idea to demo in a matter of minutes

Initial release date: 19 July 2020

## Description

The goal of this project is to enable users to create cool web demos with their GPT-3 ideas by **only writing a few lines of Python.** This project addresses the following issues:

1. Automatically formatting a user's inputs and outputs so that the model can effectively pattern-match
2. Creating a web app for a user to deploy locally and showcase their idea

Here's a quick example of priming GPT to convert English to LaTeX:

```
# Construct GPT object and show some examples
gpt = GPT(engine="davinci",
          temperature=0.5,
          max_tokens=100)
gpt.add_example(Example('Two plus two equals four', '2 + 2 = 4'))
gpt.add_example(Example('The integral from zero to infinity', '\\int_0^{\\infty}'))
gpt.add_example(Example('The gradient of x squared plus two times x with respect to x', '\\nabla_x x^2 + 2x'))
gpt.add_example(Example('The log of two times x', '\\log{2x}'))
gpt.add_example(Example('x squared plus y squared plus equals z squared', 'x^2 + y^2 = z^2'))

# Define UI configuration
config = UIConfig(description="Text to equation",
                  buttonText="Translate",
                  placeholder="x squared plus 2 times x")

demo_web_app(gpt, config)
```

Running this code as a python script would automatically launch a web app for you to test new inputs and outputs with.

Technical details: the backend is in Flask, and the frontend is in React.

## Background

GPT-3 ([Brown et. al](https://arxiv.org/abs/2005.14165)) is OpenAI's latest language model. There's a [lot](https://twitter.com/sharifshameem/status/1282676454690451457) [it](https://twitter.com/jsngr/status/1284511080715362304?s=20) [can](https://twitter.com/paraschopra/status/1284801028676653060?s=20) [do](https://www.gwern.net/GPT-3), but one of the biggest pain points is in "priming," or seeding, the model with some inputs such that the model can intelligently create new outputs. Many people have ideas for GPT-3 but struggle to make them work, since priming is a new paradigm of machine learning. Additionally, it takes a nontrivial amount of web development to spin up a demo to showcase a cool idea. We built this project to make our own idea generation easier to experiment with.

## Requirements

Coding-wise, you only need Python. But for the app to run, you will need:

* API key from the OpenAI API beta invite
* Python 3
* `yarn`

Instructions to install Python 3 are [here](https://realpython.com/installing-python/), and instructions to install `yarn` are [here](https://classic.yarnpkg.com/en/docs/install/#mac-stable).

## Setup

To set up your virtual environment, do the following:

1. Create a virtual environment in the root directory: `python -m venv $ENV_NAME`
2. Activate the virtual environment: ` source $ENV_NAME/bin/activate`
3. Install requirements: `pip install -r requirements.txt`
4. To add your secret key: create a file anywhere on your computer called `openai.cfg` with the contents `OPENAI_KEY=$YOUR_SECRET_KEY`, where `$YOUR_SECRET_KEY` looks something like `sk-somerandomcharacters`. If you are unsure what your secret key is, navigate to the [API docs](https://beta.openai.com/developer-quickstart) and copy the token displayed next to the "secret" key type.
5. Set your environment variable to read the secret key: run `export OPENAI_CONFIG=/path/to/config/openai.cfg`

To verify that your environment is set up properly, navigate to one of the scripts in the `examples` directory. Run one of them:

`python run_latex_app.py`

A new tab should pop up in your browser, and you should be able to interact with the UI! To stop this app, run ctrl-c or command-c in your terminal.

## Quickstart

## Contributions

We actively encourage people to contribute by adding their own examples or even adding functionalities to the modules. Please make a pull request if you would like to add something, or create an issue if you have a question. We will update the contributors list on a regular basis.

## Authors

The following authors have committed 20 lines or more (ordered according to the Github contributors page):

* Shreya Shankar
* Bora Uyumazturk

