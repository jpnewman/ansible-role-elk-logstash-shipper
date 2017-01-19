### Testing role 'jpnewman.elk-logstash-shipper' template

~~~
mkdir tmp

ansible-playbook ./test_template.yml -i "127.0.0.1," -c local -vvv
~~~
