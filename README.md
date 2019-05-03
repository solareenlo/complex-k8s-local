# complex-k8s-local
ローカル環境でKubernetesを使って, Nginx, React, Node.js, Redis, Postgresを1つのNode内で動かしてみた例.

## ダイアグラム
![ダイアグラム](https://github.com/solareenlo/complex-k8s-local/blob/master/images/complex-k8s-diagram.png)

## Requirement
**Ubuntu** (Install: https://jp.ubuntu.com/download)
```bash
cat /etc/os-release
> NAME="Ubuntu"
> VERSION="18.04.2 LTS (Bionic Beaver)"
> ID=ubuntu
> ID_LIKE=debian
> PRETTY_NAME="Ubuntu 18.04.2 LTS"
> VERSION_ID="18.04"
> HOME_URL="https://www.ubuntu.com/"
> SUPPORT_URL="https://help.ubuntu.com/"
> BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
> PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
> VERSION_CODENAME=bionic
> UBUNTU_CODENAME=bionic
```

**Docker** (Install: https://docs.docker.com/install/linux/docker-ce/ubuntu/)
```bash
docker -v
> Docker version 18.09.5, build e8ff056
```

**VirtualBox 6.0.6 for Linux** (Install: https://www.virtualbox.org/wiki/Linux_Downloads)

**kubectl** (Install: https://kubernetes.io/docs/tasks/tools/install-kubectl/)
```bash
kubectl version
> Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.1", GitCommit:"b7394102d6ef778017f2ca4046abbaa23b88c290", GitTreeState:"clean", BuildDate:"2019-04-08T17:11:31Z", GoVersion:"go1.12.1", Compiler:"gc", Platform:"linux/amd64"}
> Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.1", GitCommit:"b7394102d6ef778017f2ca4046abbaa23b88c290", GitTreeState:"clean", BuildDate:"2019-04-08T17:02:58Z", GoVersion:"go1.12.1", Compiler:"gc", Platform:"linux/amd64"}
```

**minikube** (Install: https://kubernetes.io/docs/tasks/tools/install-minikube/)
```bash
minikube version
> minikube version: v1.0.1
```

## Usage
```bash
minikube start
git clone git@github.com:solareenlo/complex-k8s-local.git
git cd complex-k8s-local
# 以下でingress-nginxをダウンロード
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
minikube addons enable ingress
# 以下でk8sディレクトリに入っている設定ファイルを用いて色々起動
kubectl apply -f k8s
minikube ip
> 000.111.222.333
```
そして, Chromeで`000.111.222.333`を開く.
