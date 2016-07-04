Trying to install graphite, grafana, and statsd onto ubunto using vagrant, chef solo, and berkshelf

Currently getting an error when running `vagrant up` or `vagrant provision`

```
==> default: NoMethodError
==> default: -------------
==> default: undefined method `[]' for nil:NilClass
==> default:
==> default:
==> default: Cookbook Trace:
==> default:
==> default: ---------------
==> default:   /var/chef/cache/cookbooks/nginx/recipes/ohai_plugin.rb:27:in `from_file'
==> default:   /var/chef/cache/cookbooks/nginx/recipes/default.rb:21:in `from_file'
==> default:   /var/chef/cache/cookbooks/grafana/recipes/_nginx.rb:20:in `from_file'
==> default:   /var/chef/cache/cookbooks/grafana/recipes/default.rb:21:in `from_file'
==> default:
==> default: Relevant File Content:
==> default: ----------------------
==> default: /var/chef/cache/cookbooks/nginx/recipes/ohai_plugin.rb:
==> default:
==> default:  20:  #
==> default:  21:
==> default:  22:  ohai "reload_nginx" do
==> default:  23:    action :nothing
==> default:  24:    plugin "nginx"
==> default:  25:  end
==> default:  26:
==> default:  27>> template "#{node['ohai']['plugin_path']}/nginx.rb" do
==> default:  28:    source "plugins/nginx.rb.erb"
==> default:  29:    owner "root"
==> default:  30:    group "root"
==> default:  31:    mode 00755
==> default:  32:    variables(
==> default:  33:      :nginx_prefix => node['nginx']['source']['prefix'],
==> default:  34:      :nginx_bin => node['nginx']['binary']
==> default:  35:    )
==> default:  36:    notifies :reload, 'ohai[reload_nginx]', :immediately
==> default:
==> default: Platform:
==> default: ---------
==> default: x86_64-linux
```
