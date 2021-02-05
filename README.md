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
git checkout ${KUBESPRAY_RELEASE}
```

steup inventory for your cluster:
```bash
cp -rfp inventory/sample inventory/${CLUSTER_NAME}
```

Update Ansible inventory:
```bash
CONFIG_FILE=inventory/${CLUSTER_NAME}/hosts.yml python3 contrib/inventory_builder/inventory.py ${IPS[@]}
```

Install kubespray:
```bash
ansible-playbook -i inventory/${CLUSTER_NAME}/hosts.yml cluster.yml \
  -u root \
  -b -v \
  --private-key=~/.ssh/id_ed25519
```
