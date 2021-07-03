---
layout: post
title: Standford Cryptography
tags: [Standford, Coursera, ML]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---


Secure communication: 

- Web traffic: HTTPS (SSL/TLS)
- Wireless traffic: 802.11i WPA2, GSM, Bluetooth. 

Encryption files on disk: EFS, TrueCrypt

Content protection (e.g. DVD -> CSS, Blu-rey->AACS):


TSL: 
* Handshake protocal: establish shared secret key using public-key cryptography. 
* Record Layer: Transmit data using shared secret key, ensure confidentiality. 


* confidentiality and integrity: 
* Degital signatures
* Anonymous communication
* Secret multi-party party
	* Elections
	* Private auction
* Privately outsourcing computation
* Zero knowledge

Thm: Anything the can done with trusted auth, can also be done without. 


* Precisely specify threat model
* Propose a construction
* Prove that breaking construction under threat mode will solve an underlying hard problem. 


An important property of XOR: 

Thm: Y a rand. var. over $\{0,1\}^n$, X an indep. uniform var. on $\{0, 1\}^n$. Then Z:=Y XOR X is uniform var on $\{0, 1\}^n$

The birthday paradox









 
