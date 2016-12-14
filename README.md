# cookbook-firewall
Provides a set of primitives for managing firewalls and associated rules.

## Requirements
Requires Chef 12.10 or later.

## Platforms
The following platforms are supported and tested under test kitchen:
+ CentOS 7.2

## Recipes
#### firewall::default
The default recipe installs and starts a firewall.  
Just include `firewall` in your node's `run_list`:

```json
{
  "name":"my_node",
  "run_list": [
    "recipe[firewall]"
  ]
}
```

## Resources
### firewall_rule
#### Actions
+ `allow`(default action):The rule should allow matching packets.
#### Parameters
+ `name`: The matching firewall resource that this rule applies to. If `port` is not set, the rule will be used as a service name.
+ `protocol`: `:tcp`(default),`:udp`.
+ `port`: Target port number (ie. 22 to allow inbound SSH).

#### Examples

```ruby
# open standard ssh port (full describe)
firewall_rule 'ssh' do
  port     22
  protocol :tcp
  action   :allow
end

# open standard http service (port number not set)
firewall_rule 'http' do
  protocol :tcp
  action   :allow
end

```
