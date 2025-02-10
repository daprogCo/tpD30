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


