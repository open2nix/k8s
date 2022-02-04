# k8s
Quick setup for production like k8s workload on local machine including Windows/MacOs/Linux

## prerequisite

This requires the following to be installed on you local machine:

 * [virtualbox](https://www.virtualbox.org/wiki/Downloads)
 * [vagrant](https://www.vagrantup.com/downloads)
 * [ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Installation

Once you installed the prerequisite you just need to follow below command.

```
vagrant up
```

## Usage

Get inside master host

```
vagrant ssh k8s-master 
```

Check nodes and master 

```
kubectl get nodes 
```

## Documentation

For Reference Documentation

 * [kubectl-cheatsheet](https://jamesdefabia.github.io/docs/user-guide/kubectl-cheatsheet/)


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
