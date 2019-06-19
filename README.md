Nessus Agent
============

Ansible role for installing and configuring Nessus Agent.

As Tenable does not provide a standard repository to pull its agents from, it is best to host copies of them somewhere that each node can retrieve them.  You will pass a role variable for `nessus_agent_download_page` that is only the base directory for the files.  In conjunction with `nessus_agent_version` it will generate a valid URL to fetch from and removes the need to edit any defaults or tasks.


Role Variables
--------------

- `nessus_agent_key`: Key used for linking the Nessus agent to Tenable.io, Tenable.sc or Nessus Manager. This is blank by default and should be set.

- `nessus_agent_group`: Host group this agent should be added to when linking with Nessus host.

- `nessus_agent_host`: Nessus host to link with (default: `cloud.tenable.com`).

- `nessus_agent_port`: Nessus host port (default: `443`).

- `nessus_agent_download_page`: The base URL directory for the downloaded Tenable Nessus agent.

    http://us-east.manta.joyent.com/daren.darrow@joyent.com/public/tenable/

- `nessus_agent_linux_tmp`: /tmp

- `nessus_agent_version`: 7.1.0

Example Playbook
----------------

    - hosts: all
      become: yes
      roles:
         - role: ansible-role-nessus-agent
           nessus_agent_key: xxxxxxxxx
           tags: nessus-agent
