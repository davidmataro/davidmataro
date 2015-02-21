---
layout: post
status: publish
published: true
title: Vyatta - Open Networking
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 249
wordpress_url: http://davidmataro.loc/?p=249
date: !binary |-
  MjAxMC0xMi0xMyAxNjoyNDozMSArMDAwMA==
date_gmt: !binary |-
  MjAxMC0xMi0xMyAxNjoyNDozMSArMDAwMA==
tags: []
comments: []
---
<p><a title="vyatta" href="http://http://www.vyatta.org/">Vyatta</a> es un sistema operativo de red open source que permite la gestión de enrutamiento IPv4 e IPv6, la gestión de reglas de firewall, de vpn con <a title="ipsec" href="http://en.wikipedia.org/wiki/IPsec">IPSec</a> y <a title="openvpn" href="http://openvpn.net/">OpenVPN</a>, entre otras funcionalidades.<br />
Este se puede instalar tanto sobre un servidor físicos como sobre un hypervisor como <a title="vmware" href="http://www.vmware.com/">vmware</a>, <a title="xen" href="http://www.xen.org/">xen</a> o <a title="kvm" href="http://www.linux-kvm.org/page/Main_Page">kvm</a>, permitiendo disponer de servicios de seguridad de red en entornos virtualizados y en entornos cloud.<br />
Entre las funcionalidades más destacadas están:<br />
Servicios IP:</p>
<ul>
<li>SSH: permite el acceso remoto al Vyatta de manera segura.</li>
<li>Telnet: permite el acceso remoto al Vyatta.</li>
<li>DHCP: servidor para la asignación dinámica de direcciones IP.</li>
<li>DNS: servidor de nombres de dominio.</li>
<li>NAT: Servicio de traslación de direcciones IP.</li>
<li>Web caching: servidor proxy para la aceleración de la navegación y para el filtrado de direcciones URL.</li>
</ul>
<p>Servicio de enrutamiento:</p>
<ul>
<li>Enrutamiento básico.</li>
<li>Protocolo de enrutamiento BGP (Border Gateway Protocol).</li>
<li>Protocolo de enrutamiento OSPF (Open Shortest Path First).</li>
<li>RIP (Routing Information Protocol).</li>
<li>Políticas de enrutamiento.</li>
</ul>
<p>Servicios de seguridad:</p>
<ul>
<li>Firewall: IPv4, IPv6 y por zonas.</li>
<li>Seguridad: detección de intrusiones y filtrado web.</li>
</ul>
<p>Servicios de Red Privada Virtual (VPN):</p>
<ul>
<li>VPN Lan-to-Lan con IPsec.</li>
<li>Acceso remoto con PPTP.</li>
<li>Acceso remoto con L2TP y IPsec.</li>
<li>VPN Lan-to-Lan y acceso remoto con OpenVPN.</li>
</ul>
<p>QoS (Quality of Services):</p>
<ul>
<li>Traffic shape: permite controlar y restringir la anchura de banda (bandwith) de las conexiones salientes.</li>
<li>Traffic límite: permite controlar y restringir la anchura de banda (bandwith) de las conexiones entrantes.</li>
</ul>
<p>Servicios de alta disponibilidad:</p>
<ul>
<li>WAN Load balancing: permite encritar el tráfico saliente a través de diferentes proveedores.</li>
<li>VRRP (Virtual ruteros Redundancy Protocol): permite que un cluster de Vyattas, estos actúen como un único dispositivo.</li>
<li>Clustering: permite disponer de alta disponibilidad entre dos servidores Vyatta.</li>
<li>Statefull NAT and Firewall Failover: permite replicar el estado de las conexiones entre los servidores de un cluster, de manera que en caso de error de un nodo, las conexiones se mantienen activas.</li>
<li>RAID 1: permite implementar RAID 1 de discos tanto para hardware como para software.</li>
<li>Configuration Synchronization: sincroniza la configuración entre nodos en alta disponibilidad.</li>
</ul>
<p>Con <a title="vyatta" href="http://http://www.vyatta.org/">Vyatta</a> puedes desplegar arquitecturas complejas de red a un coste muy competitivo comparado con <a title="cisco" href="http://www.cisco.com/">cisco</a> o <a title="juniper" href="http://www.juniper.net/">juniper</a> por ejemplo. Además, si requieres de apoyo, siempre puedes contratado una suscripción de soporte.</p>
