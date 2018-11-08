Role Name
=========

Role simplifies running of the Datadog monitoring agent in a docker container which comes pre-configured for monitoring container services on a docker host.

Requirements
------------

- Docker version 17.06+
- Ubuntu 14.04+
- Datadog account with valid API key
- Datadog agent container version 6+

Role Variables
--------------

- datadog_agent_image: determines the specific container image to pull from the Datadog account on Docker Hub
- datadog_agent_image_tag: the specific version of the agent container to pull/run
- data_agent_container_name: the name to give the container on each host
- data_agent_hostname: hostname to use for metrics (if autodetection fails)
- data_agent_non_local_traffic: listen to dogstatsd packets from other containers, required to send custom metrics
- data_agent_ports_mapping: bind the container's statsd ports to the hosts's IP
- matic_dd_api_key: the api key for the Matic Datadog account 
- container_memory_limit: the memory limit (if any) to set on the container to preserve host resources
- agent_restart_policy: the policy to restart the container if stopped for any reason
- collect_logs: boolean to determine if Datadog agent should collect and ship container logs
- collect_logs_all: boolean to determine if all container logs will be shipped or specific logs will be targeted via mounted config file
- collect_traces: boolean to run the trace-agent along with the infrastructure agent, allowing the container to accept traces on 8126/tcp
- collect_process: boolean to enable live process collection in the process-agent. The Live Container View is already enabled by default if the Docker socket is available

Dependencies
------------

[]

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: matic-insurance.docker-datadog
           matic_dd_api_key: e24b7fa891aa70bde374efa09
           data_agent_container_name: dd-agent
           data_agent_hostname: localhost
           data_agent_non_local_traffic: true
           data_agent_expose_ports: true
           collect_logs: true
           collect_logs_all: true
           collect_traces: true
           collect_process: false
           data_agent_ports_mapping:
             - 8125:8125/udp
             - 8126:8126/tcp


License
-------

MIT

Author Information
------------------

Matic is a communication platform that connects lenders and borrowers originating a new home loan. A borrower now knows where they are in the loan process and what they need to do to complete the loan.