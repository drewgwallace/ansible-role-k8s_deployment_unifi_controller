# Ansible Role

## Purpose
  This role is to create a Kubernetes deployment of a Unifi controller with local volume storage and NGINX TLS ingress.

----

## Execution

<pre>
    - hosts: all
      tasks:
      - include_role:
          name: drewgwallace.k8s-deployment-unifi-controller
        vars:
          database_dir: <b>/opt/data/unifi/database/</b>
          log_dir: <b>/opt/data/unifi/logs/</b>
          namespace: <b>default</b>
          url: <b>unifi.example.com</b>
          url_secret: "{{ url }}-secret"


  ### Variables:
  
    database_dir: Local directory to store the database
    log_dir: Local directory to store the log files
    namespace: Kubernetes namespace to create pod in
    url: FQDN for use by the ingress
    url_secret: Name of the k8s secret, by default it will use the URL name in the form <b>FQDN-secret</b>
</pre>

----

## Notes

  ### Look at {ansible-role-k8s_secret_cert}(https://github.com/drewgwallace/ansible-role-k8s_secret_cert) for self-signed certificate generation for integrating plays.
