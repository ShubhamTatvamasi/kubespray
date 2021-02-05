# kubespray

setup variables:
```bash
export CLUSTER_NAME="my.cluster"
export KUBESPRAY_RELEASE="release-2.15"
# add node IP here:
declare -a IPS=(1.1.1.1 2.2.2.2)
```

Prepare KubeSpray:
```bash
git clone https://github.com/kubernetes-sigs/kubespray.git
cd kubespray
git fetch --all
git checkout $KUBESPRAY_RELEASE
```

