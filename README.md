# Playbook_to_install_SuperDoctor_Normalmode
- name: Unarchive a file that is already on the remote machine
  unarchive:
    src: /tmp/SD5_5.13.0_build.1036_linux.zip
    dest: /usr/local/bin
    remote_src: yes
- name: Move foo to bar
  command: mv /tmp/SuperDoctor5Installer_5.4.0_build.703_linux_x64_20160629131648.bin SuperDoctor5Installer_5.4.0_build
- name: Changing permission SuperDoctor5Installer_5.4.0_build
  file: dest=/tmp/SuperDoctor5Installer_5.4.0_build mode=a+x
- name: Run the installer file
  become_user: root
  command: ./SuperDoctor5Installer_5.4.0_build
- name: enable service sd5
  systemd:
  name: sd5
  enabled: yes
- name: Start the service
  systemd:
    name: sd5
    state: started
    enabled: yes
