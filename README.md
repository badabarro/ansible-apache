# Projet Ansible - Déploiement Application Web Docker sous Apache

## Description

Ce projet utilise **Ansible** pour automatiser le déploiement d'une application web fonctionnant dans un container Docker sous serveur Apache. Le déploiement est conçu pour fonctionner sur différentes distributions Linux, notamment **CentOS** et **Ubuntu**.

Le projet inclut un rôle Ansible `webapp` qui gère l'installation de Docker, la configuration d'Apache et le déploiement de l'application dans un container Docker adapté à chaque système cible.

---

## Structure du projet

- `ansible-apache/`
  - `ansible.cfg` : configuration Ansible personnalisée
  - `host.yml` : inventaire des hôtes ciblés
  - `playbook.yml` : playbook principal lançant le rôle `webapp`
  - `group_vars/` et `host_vars/` : variables spécifiques par groupe et hôte
  - `roles/webapp/` : rôle Ansible contenant les tâches, handlers, variables et tests pour déployer l'application

---

Auteur

Badaoudou Barro

---
