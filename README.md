# ansible-collections

* We can either create new repo or can use existing repo.

## Initial setup.

## Source Repo setup

step 1 : create a dir called ansible_collections or with any name

 command: mkdir  ansible_collections

step 2 : Go inside the directory. 
 command: cd  ansible_collections

step 3 : create collections skeleton following by namespace.
note: we can have single namespace and single collection for all the roles  or we can have single namespace and multiple collection  for each role or we can have multiple namespace and multiple collection for each role. it is based on the busniess need. i this repo it is for single namespace and single collection for all the roles.
 command: ansible-galaxy collection init my_namespace.my_collection


step 4: fill all the roles to their respective collections and push the changes to the repo.  

## Now CD repo

step 5: In the CD repo below is the requirements.yml to install collections

## syntax
---
collections:
  # Install a collection from Git Hub
  - name: https://github.com/mohdabbas078/ansible-collections.git#/<path-of-the-collection-in-your-cource-repo>
    type: git
    version: main

## example code
---
collections:
  # Install a collection from Git Hub
  - name: https://github.com/mohdabbas078/ansible-collections.git#/ansible_collections/my_namespace1/my_collection1
    type: git
    version: main

  - name: https://github.com/mohdabbas078/ansible-collections.git#/ansible_collections/my_namespace1/my_collection2
    type: git
    version: main  

  - name: https://github.com/mohdabbas078/ansible-collections.git#/ansible_collections/my_namespace2/my_collection2
    type: git
    version: main   
    
  - name: https://github.com/mohdabbas078/ansible-collections.git#/ansible_collections/my_namespace2/my_collection2
    type: git
    version: main


step 6:  Now you can install the collections using the below command. 
    command: ansible-galaxy collection install -r requirements.yml

Usage:

---
- hosts: localhost
  remote_user: root
  collections:
    - my_namespace1.my_collection1  # Use the correct collection  

  roles:
    - uptime-checksss  # Correctly reference the role