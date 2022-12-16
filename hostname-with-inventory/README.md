# Use GCP plugin inventory

This solution use tunnel-through-iap to ssh and scp to remote compute.

## Configure Ansible:
    The configuration resides in the ansible.cfg. 
    
    In this file we enable the gcp_compute plugin and set scripts for gcp ssh and scp using tunnel-through-iap.

## ssh and scp commands
    In the misc directory you have scripts to generate the gcloud command.

## Create the inventory file.
    Check the demo.gcp.yaml. 

    This inventory creates 2 groups `_controller` and `_hub`, defaults groups are also created `all` and `ungrouped`.

    You can see the inventory by running 
    ```
    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/credentials
    ansible-inventory -i demo.gcp.yaml --graph
    ```

## Playbook
    The hostname.yaml playbook just ssh the hosts (all/_controller/_hub/ungrouped) and run the `hostname` cmd.

    ```
    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/credentials
    ansible-playbook -i demo.gcp.yaml hostname.yaml
    ```