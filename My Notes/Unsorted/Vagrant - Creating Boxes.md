---
tags:
  - IaC
  - Vagrant
date: 2025-02-25
---
# Vagrant - Creating Boxes

See Vagrant Docs:
- [Creating a Base Box](https://developer.hashicorp.com/vagrant/docs/boxes/base)
- [Creating a Base Box for the Virtualbox provider](https://developer.hashicorp.com/vagrant/docs/providers/virtualbox/boxes)
- [Creating a New Vagrant Box for Vagrant Cloud](https://developer.hashicorp.com/vagrant/vagrant-cloud/boxes/create)

⭐ With Vagrant, QEMU remains the best option to emulate alternate CPU architectures. This requires a plugin.
- *However... Virtualbox is the easiest to work with...*


# Base Boxes

> [!quote]+ **[Vagrant Docs - Creating a Base Box](https://developer.hashicorp.com/vagrant/docs/boxes/base)**
> There are a special category of boxes known as "base boxes." These boxes contain the bare minimum required for Vagrant to function, are generally not made by repackaging an existing Vagrant environment (hence the "base" in the "base box").
> 
> For example, the Ubuntu boxes provided by the Vagrant project (such as "bionic64") are base boxes. They were created from a minimal Ubuntu install from an ISO, rather than repackaging an existing environment.

## Creating custom Base Boxes

- **Virtualbox:**
	- `vagrant package --base YOUR_VM --output /your/target/dir/my-local-box.box`
		- Where "YOUR_VM" is the name of your target VM in Virtualbox

## Testing your custom Base Boxes

1. You can then add your freshly packaged box to Vagrant with:
```bash
vagrant box add my-local-box /path/to/my-local-box.box --provider <provider_name>
```

2. Then, make a new directory and initialize a new vagrant project like so:
```bash
mkdir vagrant-box-test
cd vagrant-box-test
vagrant init my-local-box
```

3. Then, to test the initial setup, just run `vagrant up`