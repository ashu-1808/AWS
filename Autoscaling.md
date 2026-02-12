

# AutoScaling:
```
- Autoscaling automatically adds or removes EC2 instances based on demand so your application    stays available, performant and cost efficient.
- Autoscaling monitors and automatically adjusts the capacity to maintain steady performance     at the lowest price.
- AWS autoscaling monitors application and scales AWS server automatically.
- Autoscaling is region specific.
- Autoscaling enables elasticity by scaling horizontally by adding or termination of an instance.
- Autoscaling Group
  - Desired = 2
  - Minimum = 1
  - Maximum = 4
```
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/cb6fd83dadf23392c413611147fb4fcf7c2aed07/autoscaling-group.png)





## Scaling Types

 ```
1. Vertical scaling – Servers capacity increase
2. Horizontal scaling – Increasing number of servers
 ```
![image alt](https://github.com/Ashu-1808/AWS-cloud-computing-for-devops/blob/30ac357b94dce5db2262d8cfc8f928e7b43ce2b6/Scaling%20types.png)


| Feature            | Vertical Scaling                                          | Horizontal Scaling                     |
| ------------------ | --------------------------------------------------------- | -------------------------------------- |
| Definizione        | Aumenta la capacità del singolo server                    | Aumenta il numero di server            |
| Come scala         | Upgrade hardware / instance size (small → medium → large) | Aggiunge nuove istanze                 |
| Processo           | Manuale, spesso richiede restart                          | Automatico, scale on demand            |
| Downtime           | Possibile durante upgrade                                 | Minimo o assente                       |
| Fault Tolerance    | Single point of failure                                   | Alta disponibilità (ridondanza)        |
| Limite di crescita | Limitato dall’hardware massimo disponibile                | Quasi illimitato                       |
| Complessità        | Più semplice da gestire                                   | Più complesso (load balancer, sync)    |
| Ideale per         | Carichi prevedibili, app piccole                          | Traffico variabile, sistemi enterprise |


---

