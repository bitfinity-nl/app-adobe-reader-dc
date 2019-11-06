# app-adobe-reader-dc
Adobe Acrobat Reader DC software is the free global standard for reliably viewing, printing, and commenting on PDF documents.

Howto
----------------
Use the "public" option for using the public repository (Default).

Use the "private" option for your private repository. This option is designed for a 
controlled environment (e.g. RDS / VDI) with an own (internal)webserver for hosting 
packages and more granular configurations.  

1. Add variable {{ def_ans_repo }} to your group_vars or change it in your playbook or role.
2. Zip all files in 1 file.
3. Upload the file to the web/download server.
4. Edit defaults/main.yml to your needs.
5. Add the role to your playbook.

* Modify file tasks/additional-tasks.yml for specific settings.

Example Playbook
----------------

This is an basic example, how to use the role:

    - hosts: windows_computers

      vars:

      roles:
        - app-adobe-reader-dc



This is an example how to use the role with custom variable(s):

    - hosts: windows_computers
      become: true

      vars:
        # -- custom settings - app-adobe-reader-dc --
        pkg_repository_type: 'private'

      roles:
        - app-adobe-reader-dc
        
        
This is an example how to use the role to uninstall the application:

    - hosts: windows_computers
      become: true

      vars:
        # -- custom settings - app-adobe-reader-dc --
        pkg_state: 'absent'

      roles:
        - app-adobe-reader-dc

Source(s)
----------------
* ftp://ftp.adobe.com/pub/adobe/
