# ft-ansible-playbook

This repository contains list of re-usable Ansible playbooks developed at Fafadia Tech. 

The main reasons why we've created this repository are:

1. Provide reference implementation of playbooks going ahead
1. Automate mundane tasks of setting up different software components without needing to duplicate scripts
1. Improve our DevOps

We've organized plays into different components as opposed to single repository with consolidated plays because of following reasons:

1. Maintain separation of concerns
1. Allow independent development {till we've completed testing and release}

## Supported Plays

Right now we're supporting:

1. `solr`: Apache Solr 4.X
1. `odoo`: Odoo 9.0

## Authors

1. Jitendra Varma
1. Yogesh Panchal