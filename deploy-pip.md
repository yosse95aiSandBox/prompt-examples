## ユーザーデータ
コピーボタンからコピーしてください。
```bash
#!/bin/bash
sudo dnf install -y gcc zlib-devel bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel 
sudo dnf install -y git 

USER=ec2-user
sudo -u ${USER} -i git clone https://github.com/pyenv/pyenv.git /home/${USER}/.pyenv
sudo -u ${USER} -i echo 'export PYENV_ROOT="$HOME/.pyenv"' >> /home/${USER}/.bash_profile
sudo -u ${USER} -i echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> /home/${USER}/.bash_profile
sudo -u ${USER} -i echo 'eval "$(pyenv init -)"' >> /home/${USER}/.bash_profile
sudo -u ${USER} -i source /home/${USER}/.bash_profile
sudo -u ${USER} -i TMPDIR="${PWD}/tmp" pyenv install 3.11.5
sudo -u ${USER} -i pyenv global 3.11.5
sudo -u ${USER} -i pyenv rehash


sudo -u ${USER} -i pip install -U pip
sudo -u ${USER} -i pip install langflow==0.6.10
sudo -u ${USER} -i python -m langflow run --port 8080 --host 0.0.0.0
aws configure set region us-west-2
```
