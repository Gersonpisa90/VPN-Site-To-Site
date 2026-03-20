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


## Direccionamieto en Equipos
-----

### RED Santo Domingo

Para configurar esta red usa el FortiGate como servidor DHCP, y el direccionamiento que use fue 10.15.29.0/28


<img width="659" height="360" alt="image" src="https://github.com/user-attachments/assets/a92e0aaf-7229-48c9-96ae-b8246469fcd7" />



<img width="630" height="454" alt="image" src="https://github.com/user-attachments/assets/a889ecf7-eba1-452a-a893-b4abc9bfdc43" />


Prueba de conectividad de una pc al Fortigate-SD:


<img width="512" height="217" alt="image" src="https://github.com/user-attachments/assets/256eaace-55ba-4350-8088-aa52a3713add" />





-------
### RED Santiago

Para configurar esta red usa el FortiGate como servidor DHCP, y el direccionamiento que use fue 10.15.30.0/28

<img width="665" height="364" alt="image" src="https://github.com/user-attachments/assets/7f7af3ee-0f9c-4780-8f0b-5561f0a02268" />



<img width="699" height="345" alt="image" src="https://github.com/user-attachments/assets/1ac2d135-098b-4665-9efb-bae9e966a393" />



Prueba de conectividad de una pc al Fortigate-ST:

<img width="508" height="204" alt="image" src="https://github.com/user-attachments/assets/33122cf2-1594-4dbb-8747-9de5298e45ff" />


-----

### RED WAN En el Fortigate-SD

para esta use una ip publica de claro real

<img width="676" height="431" alt="image" src="https://github.com/user-attachments/assets/79a2f33c-653d-494e-9241-b08eecb3b8fc" />

Prueba de conectividad con el ISP-CLARO:

<img width="599" height="379" alt="image" src="https://github.com/user-attachments/assets/6451e0ad-8ca1-434f-bfaf-e5a456c7c4d5" />



-----

### RED WAN En el Fortigate-ST

para esta use una ip publica de claro real

<img width="626" height="461" alt="image" src="https://github.com/user-attachments/assets/9df634f0-7b4c-41d9-a2b1-d6d3223848cc" />

Prueba de conectividad con el ISP-CLARO:

<img width="571" height="355" alt="image" src="https://github.com/user-attachments/assets/326d46c9-3153-4480-90b4-800f551a4273" />


-------

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

-----
## Configuracion de la VPN-SITE-TO-SITE en el FORTIGATE-SD
-----

<img width="630" height="477" alt="image" src="https://github.com/user-attachments/assets/744498cf-0bb2-4644-b77d-c767f1262f27" />


<img width="644" height="212" alt="image" src="https://github.com/user-attachments/assets/7d98fc37-0203-405a-9319-37d007e9079a" />


<img width="654" height="249" alt="image" src="https://github.com/user-attachments/assets/18ea49c5-91db-4257-9fa7-835fadec8b11" />


<img width="633" height="89" alt="image" src="https://github.com/user-attachments/assets/697443d5-e8d1-4bf0-afe4-3ab19346ef87" />



<img width="663" height="370" alt="image" src="https://github.com/user-attachments/assets/10f8c33b-93da-4608-9cf7-aff539144e4b" />


<img width="643" height="460" alt="image" src="https://github.com/user-attachments/assets/5a20aca1-7a15-4ed1-a7a5-29b38e78a8fb" />


<img width="1487" height="201" alt="image" src="https://github.com/user-attachments/assets/3720cbca-503b-46bb-904e-a88f586558e7" />

-----
## Configuracion de la VPN-SITE-TO-SITE en el FORTIGATE-ST
-----

<img width="643" height="482" alt="image" src="https://github.com/user-attachments/assets/a02a5a0f-1b2c-43c2-9510-24459f9d1e18" />

<img width="639" height="208" alt="image" src="https://github.com/user-attachments/assets/9db70907-a0e2-4585-9663-d8fc8f845647" />

<img width="638" height="252" alt="image" src="https://github.com/user-attachments/assets/d721dc1e-6b1a-4214-878d-7d3cbccf1e96" />

<img width="640" height="452" alt="image" src="https://github.com/user-attachments/assets/3a60ec41-2b15-458b-9d4b-e4a818dc5b02" />

<img width="649" height="476" alt="image" src="https://github.com/user-attachments/assets/5d77fd0c-8550-4ec1-9395-f139c89adbca" />

<img width="1596" height="212" alt="image" src="https://github.com/user-attachments/assets/de370396-cd72-43b8-b316-1f56c968cb8c" />

# REQUISITOS PARA FINALIZAR EL LAB
--------

**Configurar comunicación entre LANs mediante enlaces VPN Client-To-Site**

<img width="850" height="457" alt="image" src="https://github.com/user-attachments/assets/75809271-f585-4ba2-b8ff-0ffc2da80128" />


<img width="850" height="469" alt="image" src="https://github.com/user-attachments/assets/09a8ffd1-4644-4584-b643-7337077d7949" />

**Probar conectividad entre redes LAN mediante trace-route**

<img width="627" height="249" alt="image" src="https://github.com/user-attachments/assets/5b3e90b4-895a-4772-bc54-7ad547392357" />

-------
# VIDEO
------

https://www.youtube.com/watch?v=qdU17G2VZMI

