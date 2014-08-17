---
layout: post
title: Vagrant cluster config 
date: 2014-08-17 16:27:31
disqus: y
---

场景：在单个配置中设置多个虚拟机

---

配置示例：

{% highlight ruby %}
# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

domain   = 'example.com'

nodes = [
  { :hostname => 'mysql1', :ip => '192.168.0.42'},
  { :hostname => 'mysql2', :ip => '192.168.0.43'},
  { :hostname => 'mysql3', :ip => '192.168.0.44'},
]

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |node_config|
      node_config.vm.box = 'base'
      node_config.vm.host_name = node[:hostname] + '.' + domain
      node_config.vm.network "private_network", ip: node[:ip]

      memory = node[:ram] ? node[:ram] : 512;
      node_config.vm.provider "virtualbox" do |vb|
        vb.customize [
          'modifyvm', :id,
          '--name', node[:hostname],
          '--memory', memory.to_s
        ]
      end
    end
  end

  config.vm.provision "puppet"
end
{% endhighlight %}

具体命令可以只针对某个虚拟机执行，比如 

```
$ vagrant up mysql1
```
