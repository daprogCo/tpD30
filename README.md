# Déploiement d'un pipeline CI/CD sur AWS pour une application ReactJS

## Introduction

Le CI/CD (Continuous Integration / Continuous Deployment) est un ensemble de processus automatisés qui facilitent le développement, les tests et le déploiement des applications logicielles. Il s'agit d'un élément essentiel des pratiques de développement modernes, permettant aux équipes de livrer des changements de code plus fréquemment, de manière fiable et avec une meilleure qualité.

## Étapes pour créer un pipeline CI/CD

1. **Choisir un projet à déployer sur GitHub**
2. **Créer des rôles IAM pour EC2 et CodeDeploy**
3. **Créer une instance EC2**
4. **Créer AWS CodePipeline**
5. **Créer AWS CodeBuild**
6. **Créer AWS CodeDeploy**

---

## Projet GitHub

Afin d'établir et de valider efficacement un pipeline CI/CD, plusieurs étapes essentielles doivent être suivies. Il est important de comprendre les particularités du projet, telles que le langage de programmation et le framework utilisés.

- Les projets **frontend** utilisent souvent des frameworks comme **ReactJS, VueJS ou AngularJS**.
- Les projets **backend** reposent sur des frameworks comme **Django, Flask ou SpringBoot**.

Les différences entre ces frameworks impliquent des approches distinctes pour le déploiement. Ainsi, un **ingénieur DevOps** doit bien comprendre les exigences de chaque framework avant de créer un pipeline CI/CD. Cela garantit une intégration et un déploiement fluides.

---

## Cloner et pousser le projet sur GitHub

Pour tester le pipeline CI/CD, il faut cloner et pousser le projet dans votre propre **repository GitHub**.

```bash
git clone https://github.com/daprogCo/tpD30.git
```

## Création des rôles IAM

1. **Créer un rôle IAM pour EC2 et y attacher une politique permettant l'accès à S3.**
2. **Créer un rôle IAM pour CodeDeploy et y attacher la politique AmazonEC2RoleforAWSCodeDeploy.**

Ces rôles permettront à EC2 d'accéder à S3 et à CodeDeploy de gérer les déploiements sur l'instance EC2.

## Lancer une instance EC2

1. **Créer une instance EC2 (dans ce projet, nous utiliserons un serveur Ubuntu).**
2. ** Attacher le rôle IAM créé précédemment pour EC2.**
3. **Se connecter à l'instance via AWS Management Console et exécuter les commandes suivantes :**
   ```bash
   sudo adduser ec2-user
   ```
4. **Installer l'agent CodeDeploy en suivant les instructions d'AWS :**
   📌 [Documentation officielle](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install-ubuntu.html)

6. **Vérifier le statut de l’agent CodeDeploy :**
      ```bash
   sudo service codedeploy-agent status
   ```

## Création du pipeline CI/CD avec AWS CodePipeline, CodeBuild et CodeDeploy

### AWS CodePipeline

AWS **CodePipeline** est un service de CI/CD permettant d'automatiser le processus de **build, test et déploiement**.

- **Créer un pipeline** depuis **AWS CodePipeline**.
- **Connecter le pipeline à GitHub**.

### AWS CodeBuild

- **Créer un projet CodeBuild**.
- **Définir le fichier `buildspec.yml`** (ou entrer les commandes de build dans la console AWS).

### AWS CodeDeploy

AWS **CodeDeploy** est un service qui automatise le déploiement des applications sur **EC2**.

---

### Fichier `appspec.yml`

Le fichier **`appspec.yml`** est utilisé par **CodeDeploy** pour définir les étapes du **déploiement**.

---

### Créer l'application CodeDeploy

1. **Naviguer vers AWS CodeDeploy** et **créer une application** avec un **groupe de déploiement**.
2. **Sélectionner le rôle IAM** que nous avons créé pour **CodeDeploy**.
3. **Connecter CodeDeploy à CodePipeline** et **finaliser la configuration**.

---

### Vérifier le déploiement

Après la création du pipeline :

- **Vérifier les logs de déploiement** sur **CodeDeploy**.
- **Consulter le bucket S3** où les **artifacts** sont stockés.
- **Se connecter à l'instance EC2** et copier l'**adresse IP publique**.
- **Ouvrir un navigateur et accéder à l'application ReactJS**.

