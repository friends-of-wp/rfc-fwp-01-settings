# RFC-FWP-01 - Plugin Configuration

The request for comments describes a configuration standard for WordPress plugins.

In the best case, this proposal should go into the WordPress core, but a good and easy to implement intermediate step would be to implement it via a library that can be used by plugins.

## Motivation

When creating WordPres plugins, it is currently the case that each developer has to take care of the extension configuration pages themselves. WordPress offers functionalities that make this very easy, but the level of automation is still low.

The situation is different with other CMS or store systems. Here you can create standard configuration via XML or YAML files very easily. [Shopware](https://developers.shopware.com/developers-guide/plugin-configuration/) should be mentioned here as an excellent example.

## Benefits

- **Easy creation of settings pages**: Currently such pages have to be created by hand and can be very individual. Simple settings pages should be able to be created entirely from a configurations file.


- **CLI usage**: Once the configuration is standardized, the interface in which the user makes the settings is interchangeable. This means that it can just as well be done on the command line. This would make it easier for hosters to install preconfigured plugins or for agencies to automate standard workflows.


- **Config on WordPress installation**: Just like "CLI usage", being detached from the actual frontend can bring great advantages when installing WordPress.  Pre-installed plugins can already be configured uniformly during the installation process

## Requirements

- **Open Source** - This library is open source and everybody should have access to it.


- **Complete** - All standard configuration field types should be included. E.g. integer, url, string, email, range, image.


- **Extensible** - It should be very easy to extend the system with individual fields types.


- **CLI Tool**: There should be a CLI tool that can be used to configure via CLI from the beginning on.

## Examples

This example shows how a settings configuration can look like in YAML format.

```yaml
settings:
  
  shutdown:
    
    shutdown_condition:
      type: integer
      default: 200
      tooltip: "If the score is bigger than this value the system shuts down."
      constraints:
        min_value: 0
        
    email_on_shutdown:
      type: email
      
    public_key:
      type: individual
      settings_class: myPlugin\Elements\PublicKeySetting
```
