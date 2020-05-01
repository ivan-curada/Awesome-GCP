# Associating SSH Keys from GCP Cloud Shell to Github

The GCP Cloud Shell has a internal SSH key named `compute_engine_...pub` but this will not be used in associating SSH keys to Github. We must generate the `id_rsa.pub` SSH key for Github to recognize. 

Just follow the steps in generating SSH key and adding to the ssh-agent.

<https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent>