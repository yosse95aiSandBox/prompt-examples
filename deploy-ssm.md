## SSMから起動
コピーボタンからコピーしてください。
```bash
sudo dnf install -y gcc zlib-devel bzip2-devel readline-devel sqlite sqlite-devel openssl-devel tk-devel libffi-devel xz-devel

sudo dnf install -y git

curl https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib' >> ~/.bashrc

source ~/.bashrc
CFLAGS=-I/usr/include/openssl LDFLAGS=-L/usr/lib pyenv install -v 3.11.5
 
pyenv global 3.11.5
pyenv rehash

aws configure set region us-east-1

pip install -U pip
pip install langflow==0.6.10
langflow run --port 8080
```
