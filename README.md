# F5 TMOS upgrade playbooks 

## Notes 

Requires the F5 ansible collection:
https://clouddocs.f5.com/products/orchestration/ansible/devel/usage/getting_started.html

It's a good idea to re-activate the license before a software upgrade, I don't handle this yet:
https://support.f5.com/csp/article/K7752

Smaller TMOS VEs (2 vCPU/8 GB RAM) might not have enough resources for iControl REST to function properly (with default settings)- modify management provisioning to 'large':
https://support.f5.com/csp/article/K26427018

If you are downgrading TMOS, your config won't carry across:
https://support.f5.com/csp/article/K14568

I have split the upgrade and activation tasks, as I think most people would want to schedule these seperately.

## Usage

Install f5 collection:  

`ansible-galaxy collection install f5networks.f5_modules`

Run the software upload/installation:  

`ansible-playbook -i hosts.ini upgrade.yaml`

Activate the new version:  

`ansible-playbook -i hosts.ini activate.yaml`

