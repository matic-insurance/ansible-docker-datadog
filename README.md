Role Name
=========

Role simplifies running of the Datadog monitoring agent in a docker container which comes pre-configured for monitoring container services on a docker host.

Requirements
------------

- Docker version 17.06+
- Ubuntu 14.04+
- Datadog account with valid API key

Role Variables
--------------

- datadog_agent_image: determines the specific container image to pull from the Datadog account on Docker Hub
- datadog_agent_image_tag: the specific version of the agent container to pull/run
- data_agent_container_name: the name to give the container on each host
- matic_dd_api_key: the api key for the Matic Datadog account 
- container_memory_limit: the memory limit (if any) to set on the container to preserve host resources
- agent_restart_policy: the policy to restart the container if stopped for any reason

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
           data_agent_container_name: datadog-docker-agent

License
-------

MIT

Author Information
------------------

Matic is a communication platform that connects lenders and borrowers originating a new home loan. A borrower now knows where they are in the loan process and what they need to do to complete the loan.