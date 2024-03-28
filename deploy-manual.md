# コマンド集
ハンズオン内で利用するコマンドをコピーできるようにしてあります。

コピーボタンからコピーしてください。

# 前準備
## aws cli の設定 1 (windows)
```cmd
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

## aws cli の設定 2 (windows)
```cmd
aws configure
```

## Session Manager Plugin の設定 (windows)
```cmd
curl https://s3.amazonaws.com/session-manager-downloads/plugin/latest/windows/SessionManagerPluginSetup.exe -o SessionManagerPluginSetup.exe
.\SessionManagerPluginSetup.exe

```

## aws cli から EC2 への接続 (windows)
```cmd
aws ssm start-session --target <instance-id> --document-name AWS-StartPortForwardingSessionToRemoteHost --parameters portNumber=8080,localPortNumber=8080
```

# Langflowの起動、再起動

## SSM上から起動（ユーザーデータを利用しない場合）
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

## SSM上から起動（再起動時）
```bash
langflow run --port 8080
```
