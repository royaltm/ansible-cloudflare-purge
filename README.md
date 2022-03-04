Cloudflare Purge
================

Ansible role for purging files from caches on CloudFlare servers

Requirements
------------

* httplib2 (ansible uri module)


Role Variables
--------------

* `cloudflare_purge_zone` - a CloudFlare zone ID
* `cloudflare_purge_email` - a CloudFlare authorization email
* `cloudflare_purge_key` - a CloudFlare authorization API key
* `cloudflare_purge_from_file` - a path to file containing list of urls to purge in YAML format
* `cloudflare_purge_urls` - alternatively provide direct list of urls to purge
* `cloudflare_purge_tags` - list of tags to purge
* `cloudflare_purge_hosts` - list of hosts to purge
* `cloudflare_purge_prefixes` - list of prefixes to purge


Example Playbook
----------------

Providing external yml file with urls:

    - hosts: example
      vars:
        cloudflare_purge_email: "YOUR EMAIL"
        cloudflare_purge_key: "YOUR KEY"
      roles:
        - role: advertine.cloudflare-purge
          cloudflare_purge_zone: "YOUR ZONE ID"
          cloudflare_purge_from_file: "/path/to/urls.yml"


Providing direct list of urls:

    - hosts: example
      vars:
        cloudflare_purge_email: "YOUR EMAIL"
        cloudflare_purge_key: "YOUR KEY"
      roles:
        - role: advertine.cloudflare-purge
          cloudflare_purge_zone: "YOUR ZONE ID"
          cloudflare_purge_urls:
            - "https://example.com/path/to/purged/file"

Providing list of tags or prefixes or list(enterprise only):

    - hosts: example
      vars:
        cloudflare_purge_email: "YOUR EMAIL"
        cloudflare_purge_key: "YOUR KEY"
      roles:
        - role: advertine.cloudflare-purge
          cloudflare_purge_zone: "YOUR ZONE ID"
          cloudflare_purge_tags:
            - tag1
            - tag2
          cloudflare_purge_prefixes:
            - "test.yahoo/asd1" 

License
-------

BSD

Author Information
------------------

Rafał Michalski

