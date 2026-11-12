# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom : GROMAIRE Etienne** 
**Groupe : RS2**

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
   > Il y a 3 noeuds : k3d-lab-agent-0    Ready    <none>          3m30s   v1.35.5+k3s1	
	>k3d-lab-agent-1    Ready    <none>          3m30s   v1.35.5+k3s1
	>k3d-lab-server-0   Ready    control-plane   3m34s   v1.35.5+k3s1

k3d-lab-server-0 (rôle control-plane) : c’est le server, le cerveau du cluster. Il héberge l’API server (commandes kubectl), le scheduler (sur quel nœud placer un pod), le controller manager, et etcd (la base de données du cluster).
k3d-lab-agent-0 et k3d-lab-agent-1 (rôle <none>) : ce sont les workers. Ce sont eux qui font tourner les pods, donc tes applications.

2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
   >
@EGromaire ➜ /workspaces/kubernetes_tp1 (main) $ docker ps
CONTAINER ID   IMAGE                            COMMAND                  CREATED         STATUS         PORTS                                                              NAMES
156aef03955e   ghcr.io/k3d-io/k3d-proxy:5.9.0   "/bin/sh -c nginx-pr…"   5 minutes ago   Up 4 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp, 0.0.0.0:41799->6443/tcp   k3d-lab-serverlb
50588a82c9ff   rancher/k3s:v1.35.5-k3s1         "/bin/k3d-entrypoint…"   5 minutes ago   Up 4 minutes                                                                      k3d-lab-agent-1
a32822e51010   rancher/k3s:v1.35.5-k3s1         "/bin/k3d-entrypoint…"   5 minutes ago   Up 4 minutes                                                                      k3d-lab-agent-0
65ec7fd3afdd   rancher/k3s:v1.35.5-k3s1         "/bin/k3d-entrypoint…"   5 minutes ago   Up 5 minutes                                                                      k3d-lab-server-0

On retrouve un loadbalancer qui répartie la charge entre les trois instances et les exposes les ports, ainsi que les trois instances de k3d avec les 2 workers et le server.


## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   >
4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   >

## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   >
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   >

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   >
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   >

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
   ```

   ```
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
