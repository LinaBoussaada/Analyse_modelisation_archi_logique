# Architecture Microservices de DeepSeek

## Description du Projet

Ce document présente l'architecture microservices de DeepSeek, une plateforme d'intelligence artificielle avancée. L'architecture vise à assurer scalabilité, haute disponibilité et performance pour des workloads d'IA modernes.
### Warning
Après discussion avec les membres de l’équipe et le retour du DeepSeek, il apparaît que le moteur d’inférence doit être réévalué, aucun blocage n’ayant été identifié lors de nos échanges. Pour cette raison, nous proposons de séparer les responsabilités en deux services : le premier dédié au moteur d’inférence, et le second au deep learning, à utiliser lorsque la réponse n’est pas connue.

## Documents Disponibles

- **Version Initiale** : `main.tex` - Architecture de base  
- **Version Améliorée** : `main-version-ameliorer.tex` - Architecture ameliorée  

## Évolution de l'Architecture

### Version 1 → Version 2 : Améliorations du Diagramme de Composants UML

#### 1. Service Mesh
- **Changement** : Ajout d'une couche Service Mesh transversale  
- **Objectifs** : Sécuriser la communication inter-services, améliorer l'observabilité et gérer les policies automatiques (retry, circuit breaking).

#### 2. Load Balancer Intelligent
- **Changement** : Ajout d'un composant Load Balancer pour les services IA  
- **Objectifs** : Optimiser le routage vers les GPU disponibles, gérer l'auto-scaling et réduire la latence.

#### 3. Fine-tuning Service
- **Changement** : Séparation du service de fine-tuning du Training Service  
- **Objectifs** : Spécialiser le fine-tuning, optimiser les ressources et faciliter la maintenance.

#### 4. Feature Store
- **Changement** : Ajout d'un service Feature Store dédié  
- **Objectifs** : Centraliser la gestion des features, assurer cohérence et traçabilité, et favoriser la réutilisation.

#### 5. Message Broker
- **Changement** : Introduction d'un service de messagerie asynchrone  
- **Objectifs** : Découpler les services, gérer les pics de charge et favoriser l’architecture event-driven.

#### 6. Monitoring Consolidé
- **Changement** : Regroupement des services de monitoring  
- **Objectifs** : Centraliser l’observabilité, réduire la complexité et faciliter les alertes cohérentes.

#### 7. Réorganisation des Dépendances
- **Changement** : Optimisation du graphe de dépendances  
- **Objectifs** : Réduire le couplage, améliorer la modularité et optimiser les flux de données.


## Architecture Technique

### Couches Architecturales

1. **API** : Gateway et authentification  
2. **Service Mesh** : Communication sécurisée et observabilité  
3. **Services Core** : Services métier d'IA  
4. **Données** : Gestion et stockage  
5. **Infrastructure** : Services de support  

### Technologies Utilisées

- **Orchestration** : Kubernetes  
- **Service Mesh** : Istio/Envoy  
- **API Gateway** : Kong/Envoy  
- **Langages** : Python/Go  
- **Bases de données** : PostgreSQL, Redis, Vector DB (Milvus/Pinecone)  
- **Message Queue** : Apache Kafka  
- **Monitoring** : Prometheus/Grafana  
- **Logging** : ELK Stack  

## Avantages de la Version Améliorée

- Meilleure scalabilité grâce au load balancing intelligent  
- Sécurité renforcée avec Service Mesh et mTLS  
- Observabilité consolidée avec tracing distribué  
- Résilience accrue via circuit breakers et retry policies  
- Performance optimisée avec Feature Store et cache  
- Maintenabilité améliorée grâce à des services découplés  

## Déploiement

Déploiement sur Kubernetes avec les namespaces :  
- `gateway` : Services d'entrée  
- `auth` : Services d'authentification  
- `ai-services` : Services IA  
- `data-services` : Services de données  
- `infrastructure` : Services de support  

## Patterns Architecturaux

- Microservices pour le découplage et la scalabilité  
- API Gateway comme point d'entrée sécurisé  
- Service Mesh pour communication et observabilité  
- CQRS pour séparer lecture et écriture  
- Event-Driven via messages asynchrones  
- Circuit Breaker pour limiter les pannes en cascade  

## Contributeurs

| Nom & Prénom |
|--------------|
| Lina Boussaada |
| Mariem Trabelsi | 
| Chaima Ben Omrane | 
| Mariem Ajroud | 
| Hazem Hammami |

---

*Document technique sur l'architecture DeepSeek, maintenu par l'équipe système.*
