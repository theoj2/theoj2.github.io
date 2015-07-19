---
author: tjones
comments: false
date: 2013-12-31 21:31:26+00:00
layout: post
slug: ofb-encryption-newlisp-hashing-algorithm-2
title: OFB Encryption in Newlisp With A Hashing Algorithm
wordpress_id: 1077
categories:
- old
tags:
- OFB
- Old
---

Below is a bit of code that showcases how to use a block cipher in OFB mode with Newlisp.[ Because it is possible to use](http://crypto.stackexchange.com/questions/48/is-it-feasible-to-build-a-stream-cipher-from-a-cryptographic-hash-function?rq=1) a hashing function like an encryption-only "block cipher" and Newlisp has a SHA256 function in its standard libraries this code uses that hashing function.  
<!-- more -->  



`   

(module "crypto.lsp")





(define (OFBcipherPad encfunc iv key blocksneeded)
    (if (<= blocksneeded 0) 
       ("")
       (if (= blocksneeded 1)
             (encfunc (append iv key))
             (append (encfunc (append iv key)) (OFBcipherPad encfunc (encfunc (append iv key)) key (- blocksneeded 1) )))
     )
)





(define (SHA256Func data)
    (crypto:sha256 data true)
)





(define (encryptdataSHA256 data iv key , OFBpad)
     (set 'OFBpad (OFBcipherPad SHA256Func iv key (+ 1 (/ (length data))) ))
     (encrypt data (slice OFBpad 0 (length data)))
)





(println (encryptdataSHA256 "dafta" "iv" "key"))
(exit)
`
