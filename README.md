# jpnewman.elk-logstash-shipper

[![Ansible Role](https://img.shields.io/ansible/role/9591.svg?maxAge=2592000)](https://galaxy.ansible.com/jpnewman/elk-logstash-shipper/)
[![Build Status](https://travis-ci.org/jpnewman/ansible-role-elk-logstash-shipper.svg?branch=master)](https://travis-ci.org/jpnewman/ansible-role-elk-logstash-shipper)

This is a Ansible role to installs [logstash](https://www.elastic.co/products/logstash) shipper

The logstash shipper creates the following logstash configuration files: -

- 01-lumberjack-input.conf
- 02-beats-input.conf
- 03-syslog-input.conf
- 04-redis-metrics-input.conf
- 10-syslog-filter.conf
- 11-nginx-filter.conf
- 12-apache-filter.conf
- 13-artifactory-filter.conf
- 14-redis-metrics-filter.conf
- 25-shipper-filter.conf
- 29-geoip-filter.conf
- 30-redis-output.conf
- 31-stdout-output.conf

**N.B.** Currently ```13-artifactory-filter.conf``` only parses NuGet packages.

## Requirements

Ansible 2.x

## Role Variables

|Variable|Description|Default|
|---|---|---|
|```which_interface```||eth0|
|```logstash_repo_version```||2.3|
|```logstash_listen_port```||5043|
|```logstash_redis_host```||localhost|
|```logstash_redis_port```||6379|
|```logstash_redis_db```||0|
|```logstash_redis_key```||logstash|
|```logstash_redis_data_type```||channel|
|```logstash_beats_congestion_threshold```||5|
|```logstash_redis_metrics```||true|
|```logstash_with_plugin```||true|
|```logstash_debug```||false|
|```logstash_ls_heap_size```||1g|
|```logstash_ls_open_files```||16384|
|```logstash_geoip_known_locations```||[]|
|```logstash_elasticsearch_hosts```||'["localhost:9200"]'|
|```logstash_elasticsearch_index```||'logstash-%{+YYYY.MM.dd}'|
|```ssl_cert_local_directory```||files/certs|
|```ssl_cert_directory```||/etc/pki/tls/certs|
|```ssl_cert```||logstash-forwarder.crt|
|```ssl_key```||logstash-forwarder.key|
|```apt_cache_valid_time```||600|
|```geoip_database_url_path```||http://geolite.maxmind.com/download/geoip/database|
|```geoip_database_url_filename```||GeoLiteCity.dat.gz|
|```geoip_database_extracted_filename```||GeoLiteCity.dat|
|```geoip_database```||/etc/logstash/geoip/{{ geoip_database_extracted_filename }}|

## Dependencies

none

## Example Playbook

    - hosts: servers
      roles:
         - { role: jpnewman.elk-logstash-shipper, tags: ["logstash-shipper"] }

## Testing

For more information on testing the template review readme ```./tests/templates/README.md```

## License

MIT / BSD

## Author Information

John Paul Newman
