ansible-role-openshift-username-password-auth
=============================================

A role to authenticate to an OpenShift clusters with username and password to retrive an authentication token that can then be used with k8s* modules to interact with the kubernetes API and then logs out (revokes the authentication token),

Requirements
------------

Automation controller(Ansible Tower) does not currently have a native OpenShift credential type, but it does provide the ability to create custom Credential Types. The steps below show how to create a Custom Credential Type in Automation controller(Ansible Tower) to support storing the username and password used to authenticate with OpenShift. First a OpenShift Credential Type is created, and then a Credential is created using the new credential type which stores the username, password and host information.

1. Navigate to Administration > Credential Types and add a new credential type.
2. Name it OpenShift and add the following YAML in the Input Configuration:
`ls`
`
fields:
  - id: host
    type: string
    label: URL for accessing the API server
  - id: username
    type: string
    label: Username for authenticating with the API server
  - id: password
    type: string
    label: Password for authenticating with the API server
    secret: true
  - id: verify_ssl
    type: boolean
    label: Verify the API server's SSL certificates
  - id: ca_certificate
    type: string
    label: CA certificate used to verify connection to the API server
    multiline: true
required:
  - username
  - password
  - host
`
3. 

Role Variables
--------------

Dependencies
------------



Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
