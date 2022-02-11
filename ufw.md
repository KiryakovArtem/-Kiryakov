--
- name: Разрешение 80 8080 1834 порта - firewalld
  hosts: all
  become_method: sudo
  become_user: root

  tasks:
  - name: Разрешим 80 порт
    ansible.posix.firewalld:
      service: http
      permanent: yes
      state: enabled
  - name: Разрешим 8080 порт
    ansible.posix.firewalld:
      service: https
      permanent: yes
      state: enabled
  - name: Разрешим 1834 порт
    ansible.posix.firewalld:
      service: https
      permanent: yes
      state: enabled
  - name: Перезапустим service firewalld на всех узлах
    ansible.builtin.service:
      name: firewalld
      state: restarted
~                              
