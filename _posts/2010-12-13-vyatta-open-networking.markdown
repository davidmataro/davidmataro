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
wordpress_id: 125
wordpress_url: http://www.davidmataro.com/?p=125
date: !binary |-
  MjAxMC0xMi0xMyAyMzowMDowOSArMDAwMA==
date_gmt: !binary |-
  MjAxMC0xMi0xMyAyMTowMDowOSArMDAwMA==
tags: []
comments: []
---
<div id="_mcePaste"><a title="vyatta" href="http://http://www.vyatta.org/">Vyatta</a> és un sistema operatiu de xarxa open source que permet la gestió d'enrutaments IPv4 i IPv6, la gestió de regles de firewall, de vpn amb <a title="ipsec" href="http://en.wikipedia.org/wiki/IPsec">IPSec</a> i <a title="openvpn" href="http://openvpn.net/">OpenVPN</a>, entre d'altres funcionalitats.</div>
<div id="_mcePaste">Aquest es pot instal·lar tant sobre un servidor físics com sobre un hypervisor com <a title="vmware" href="http://www.vmware.com/">vmware</a>, <a title="xen" href="http://www.xen.org/">xen</a> o <a title="kvm" href="http://www.linux-kvm.org/page/Main_Page">kvm</a>, permetent disposar de serveis de seguretat de xarxa en entorns virtualitzats i en entorns cloud.</div>
<div id="_mcePaste">Entre les funcionalitats més destacades hi ha:</div>
<div>Serveis IP:</div>
<div id="_mcePaste">
<ul>
<li>SSH: permet l’accés remot al Vyatta de manera segura.</li>
<li>Telnet: permet l’accés remot al Vyatta.</li>
<li>DHCP: servidor per a la assignació dinàmica d’adreces IP.</li>
<li>DNS: servidor de noms de domini.</li>
<li>NAT: Servei de traslació d’adreces IP.</li>
<li>Web caching: servidor proxy per a la acceleració de la navegació i per al filtratge de adreces URL.</li>
</ul>
</div>
<div id="_mcePaste">Servei d’enrutament:</div>
<div id="_mcePaste">
<ul>
<li>Enrutament bàsic.</li>
<li>Protocol d’enrutament BGP (Border Gateway Protocol).</li>
<li>Protocol d’enrutament OSPF (Open Shortest Path First).</li>
<li>RIP (Routing Information Protocol).</li>
<li>Polítiques d’enrutament.</li>
</ul>
</div>
<div id="_mcePaste">Serveis de seguretat:</div>
<div id="_mcePaste">
<ul>
<li>Firewall: IPv4, IPv6 i per zones.</li>
<li>Seguretat: detecció d’intrusions i filtratge web.</li>
</ul>
</div>
<div id="_mcePaste">Serveis de Xarxa Privada Virtual (VPN):</div>
<div id="_mcePaste">
<ul>
<li>VPN Lan-to-Lan amb IPsec</li>
<li>Accés remot amb PPTP.</li>
<li>Accés remot amb L2TP i IPsec.</li>
<li>VPN Lan-to-Lan i accés remot amb OpenVPN.</li>
</ul>
</div>
<div id="_mcePaste">QoS (Quality of Services):</div>
<div id="_mcePaste">
<ul>
<li>Traffic shape: permet controlar i restringir la amplada de banda (bandwith) de les connexions sortints.</li>
<li>Traffic limit: permet controlar i restringir la amplada de banda (bandwith) de les connexions entrants.</li>
</ul>
</div>
<div id="_mcePaste">Serveis d’alta disponibilitat:</div>
<div id="_mcePaste">
<ul>
<li>WAN Load balancing: permet encritar el tràfic sortint a través de diferents proveïdors.</li>
<li>VRRP (Virtual Ruter Redundancy Protocol): permet que un cluster de Vyattas, aquests actuin com un únic dispositiu.</li>
<li>Clustering: permet disposar d’alta disponibilitat entre dos servidors Vyatta.</li>
<li>Statefull NAT and Firewall Failover: permet replicar l’estat de les connexions entre els servidors d’un cluster, de manera que en cas d’error d’un node, les connexions es mantenen actives.</li>
<li>RAID1: permet implementar RAID 1 de discos tant per hardware com per software.</li>
<li>Configuration synchronization: sincronitza la configuració entre nodes en alta disponibilitat.</li>
</ul>
</div>
<p>Amb <a title="vyatta" href="http://http://www.vyatta.org/">Vyatta</a> pots desplegar arquitectures complexes de xarxa a un cost molt competitiu comparat <a title="cisco" href="http://www.cisco.com/">cisco</a> o <a title="juniper" href="http://www.juniper.net/">juniper</a> per exemple. A més, si requereixes de suport, sempre pots contractat una subscripció de suport.</p>
