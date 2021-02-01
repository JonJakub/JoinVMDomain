#### Join CentOS into Windows Domain ####

- Spuštění playbook.yaml

Je třeba zadat vstupy:

- Domain Username + Password
- Název domény
- Domenový Controller
- Organozační skupinu (ComputerOU)
- Linux Admina


- Playbook spustí Task roles/tasks/main.yaml

Naistaluje potřebné balíčky z vars/RedHat.yml
Nakonfiguruje potřebné servicy (Samba,SSSD)
Přípojí se přes realm do domény
Nastaví sudoers




