#### Join CentOS into Windows Domain ####

Před spušťěním je třeba definovat v playbook.yaml adresu serveru který chceme připoit do domény:

- name: Join CentOS to Windows domain
  hosts: !Adresa serveru pro ktery se ma připojit!
  become: yes  


- Spuštění playbook.yaml

ansible-playbook playbook.yaml -u vmadmin --ask-pass -kK

- "-u" definujeme usera pod kterym se budou provadet operace na cilovem VM ktere ma byt připojeno do Domeny
- "--ask-pass" zepta se na heslo pro připoení přes ssh pro daneho usera
- "-kK" zepta se v případě potřeby znova na heslo pro usera pokud jsou potřeba vyšší práva

Je třeba zadat vstupy:

- Domain Username + Password  
- Název domény (example: jjon.com)
- Domenový Controller (example: adwinservertest.internal.cloudapp.net)
- Organizační skupinu (ComputerOU)
- Linux Admina


Playbook spustí Task roles/tasks/main.yaml

- Naistaluje potřebné balíčky z vars/RedHat.yml
- Nakonfiguruje potřebné servicy (Samba,SSSD,Kerberos)
- Přípojí se přes realm do domény (realm join Název domény  --user=Domain Username --computer-ou=OU=Organizační skupina )
- Nastaví sudoers (Linux Admin)


parametr no_log v roles/tasks/main.yml akplikovan aby to na vystupu neukazovalo heslo atd. 




