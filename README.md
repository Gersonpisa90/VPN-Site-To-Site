# VPN-Site-To-Site

## Topologia

<img width="849" height="699" alt="image" src="https://github.com/user-attachments/assets/df2c12f4-6302-4cfe-a7cc-b73c1c530ec1" />

Basado en la topología de red de la imagen, aquí tienes el esquema de direccionamiento IP organizado en formato Markdown (estilo GitHub):
Plan de Direccionamiento de Red1. Segmentos WAN (Interconexión ISP)

| Dispositivo | Interfaz | Dirección IP | Red / Máscara |
|---|---|---|---|
| ISP-CLARO | e0/2 | IP Pública (NAT) | Hacia Internet |
| ISP-CLARO | e0/0 | 64.32.106.1 | 64.32.106.0/24 |
| ISP-CLARO | e0/1 | 200.88.0.1 | 200.88.0.0/16 |
| FortiGate-SD | Port1 | 64.32.106.2 | 64.32.106.0/24 |
| FortiGate-ST | Port1 | 200.88.0.2 | 200.88.0.0/16 |

------------------------------
2. Site: Santo Domingo (SD)
Red LAN: 10.15.29.0/28

| Dispositivo | Interfaz | Dirección IP | Gateway |
|---|---|---|---|
| FortiGate-SD | Port2 | 10.15.29.1 (Asumida) | N/A |
| SWM-SD1 | e0/0 | IP de Gestión | 10.15.29.1 |
| Linux-SD1 | ens4 | IP Dinámica/Estática | 10.15.29.1 |
| Linux-SD2 | ens4 | IP Dinámica/Estática | 10.15.29.1 |

------------------------------
3. Site: Santiago (ST)
Red LAN: 10.15.30.0/28

| Dispositivo | Interfaz | Dirección IP | Gateway |
|---|---|---|---|
| FortiGate-ST | Port2 | 10.15.30.1 (Asumida) | N/A |
| SWM1-ST | e0/2 | IP de Gestión | 10.15.30.1 |
| Linux-ST1 | ens4 | IP Dinámica/Estática | 10.15.30.1 |
| Linux-ST2 | ens4 | IP Dinámica/Estática | 10.15.30.1 |

------------------------------


## Direccionamieto
-----

### RED Santo Domingo

Para configurar esta red usa el FortiGate como servidor DHCP, y el direccionamiento que use fue 10.15.29.0/28


<img width="659" height="360" alt="image" src="https://github.com/user-attachments/assets/a92e0aaf-7229-48c9-96ae-b8246469fcd7" />



<img width="630" height="454" alt="image" src="https://github.com/user-attachments/assets/a889ecf7-eba1-452a-a893-b4abc9bfdc43" />

### RED Santiago

Para configurar esta red usa el FortiGate como servidor DHCP, y el direccionamiento que use fue 10.15.30.0/28

<img width="665" height="364" alt="image" src="https://github.com/user-attachments/assets/7f7af3ee-0f9c-4780-8f0b-5561f0a02268" />



<img width="699" height="345" alt="image" src="https://github.com/user-attachments/assets/1ac2d135-098b-4665-9efb-bae9e966a393" />

### RED WAN En el Fortigate-SD

para esta use una ip publica de claro real

<img width="676" height="431" alt="image" src="https://github.com/user-attachments/assets/79a2f33c-653d-494e-9241-b08eecb3b8fc" />

### RED WAN En el Fortigate-ST

para esta use una ip publica de claro real

<img width="626" height="461" alt="image" src="https://github.com/user-attachments/assets/9df634f0-7b4c-41d9-a2b1-d6d3223848cc" />



### Conectividad entre Fortigate-SD to Fortigate-ST

Para hacer esto tuve que usar una ruta estatica:


**Fortigate-ST**

<img width="538" height="301" alt="image" src="https://github.com/user-attachments/assets/f7dc0093-2dbc-49ad-8880-0b8fa7602101" />


Prueba de conectividad al Fortigate-SD:

<img width="554" height="291" alt="image" src="https://github.com/user-attachments/assets/0227da9a-6561-4052-8e78-f13b7cf75ee4" />


**Fortigate-SD**

<img width="587" height="363" alt="image" src="https://github.com/user-attachments/assets/00b57189-094d-4eac-9711-947c179029af" />

Prueba de conectividad al Fortigate-ST:


<img width="553" height="320" alt="image" src="https://github.com/user-attachments/assets/2b845dd9-f95e-4503-ba39-9a410a710384" />


