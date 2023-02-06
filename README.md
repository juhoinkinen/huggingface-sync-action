# huggingface-sync-action

A GitHub action that'll sync files from a GitHub repo with the Hugging Face Hub. 🤗

A simple example repo using this can be found [here](https://github.com/nateraw/test-spaces-app). A more complex example can be seen [here](https://github.com/nateraw/my-huggingface-repos/).

## Usage

The first step is to add a Hugging Face token with write access to your repo as a GitHub Secret. Below, mine is called `HF_TOKEN`. Then, you can use this action in your repo as shown below. :)

```yaml
uses: nateraw/huggingface-sync-action@v0.0.2
with:
  # The github repo you are syncing from. Required.
  github_repo_id: ''

  # The Hugging Face repo id you want to sync to. (ex. 'username/reponame')
  # A repo with this name will be created if it doesn't exist. Required.
  huggingface_repo_id: ''

  # The type of repo you are syncing to: model, dataset, or space.
  # Defaults to space.
  repo_type: 'space'
  
  # If true and the Hugging Face repo doesn't already exist, it will be created
  # as a private repo.
  #
  # Note: this param has no effect if the repo already exists.
  private: false

  # If repo type is space, specify a space_sdk. One of: streamlit, gradio, or static
  #
  # This option is especially important if the repo has not been created yet.
  # It won't really be used if the repo already exists.
  space_sdk: 'gradio'
  
  # If provided, subdirectory will determine which directory of the repo will be synced.
  # By default, this action syncs the entire GitHub repo.
  #
  # It can be useful to sync only a subdirectory, as that means you can then sync multiple
  # Hugging Face repos from one central GitHub repo. An example can be seen here:
  # https://github.com/nateraw/my-huggingface-repos/
  #
  subdirectory: ''

# When using this action, you must provide a Hugging Face token with write access.
# Here, we provide that token, which we called `HF_TOKEN` when we added the secret to our GitHub repo.
secrets:
  hf_token: ${{ secrets.HF_TOKEN }}
```
