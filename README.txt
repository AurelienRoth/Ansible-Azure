Repo de training de préparation à l'entretien chez QAPA

Exercice de configuration de machines virtuelles (des vm de prod "vm" et une vm de monitoring "monitoring") sur le cloud Azure via Ansible

CREATION ET GESTION DES RESSOURCES

- "create_vm.yml" permet la création de l'ensemble des ressources azure et de l'accès SSH.
  Il crée ensuite les vm, il est alimenté par des variables provisionnées dans "vars/vmvars"
  Il crée une sortie enregistrée dans vars/hostvars
  Inspirations : docs ansible & blog Zwindler's Reflection

- l'inventaire est réalisé de façon dynamique avec le plugin "azure_rm", prévu au fichier de config d'Ansible ("ansible.cfg")
  les tags sont mis automatiquement selon l'OS, l'IP, et selon si la machine a été créée pour être prod/monitoring

- dans un souci d'économie des ressources dans le cadre de ce training, des fichiers yml spécifiques ont été créés
  - un fichier "start_stop_vm.yml" afin de démarrer ou arrêter les machines sans désallouer les IP
  - un ficher "destroy_gr.yml" pour détruire le groupe de ressources de ce training ainsi que tous ses composants

- un repertoire de playbooks d'essais, sans fonctions opérantes sur les ressources

PROVISIONING DES VM

- playbook "main.yml" qui prévoit l'ensemble du provisonning des vm

- un répertoire tasks avec des installs disponibles de docker et git

- un repertoire "roles" pour la configuration des Node_exporter et de prometheus
  Sources : geerlingguy & cloudalchemy

