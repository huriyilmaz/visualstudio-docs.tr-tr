---
title: 'Hata: Web sunucusu kilitli ve hata ayıklama fiilini engelliyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b85efc44b39485476154d0f41f3261b2aeb1ea7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203213"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web uygulamasına veya XML Web hizmetine adımlamak, IIS Kilitleme Aracı çalıştırıldığı ve URLScan yüklenmiş ve etkinleştirilmiş olduğundan başarısız oldu. Bu koşul, IIS 'nin hata ayıklama fiilini almasını engeller.  
  
 URLScan, IIS Web sitesi yöneticilerine gereksiz özellikleri kapatma ve sunucunun işleyeceğini HTTP isteklerinin türünü kısıtlama yeteneği sağlamak için IIS kilitleme aracı ile birlikte çalışan bir güvenlik aracıdır. URLScan güvenlik aracı, belirli HTTP isteklerini engelleyerek, zararlı olabilecek isteklerin sunucuya ulaşmasını ve hasar vermesine neden olur.  
  
 Uygulamanız Windows Server 2003 üzerinde IIS 6,0 üzerinde çalışıyorsa, IIS 6,0 aynı işlevselliği sağladığından IIS Kilitleme Aracı 'nı çalıştırmanız gerekir.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>URLScan yüklü bir Web sunucusunda hata ayıklamayı etkinleştirmek için  
  
1. Urlscan.ini dosyasını bulun. Normalde, bunu şuna benzer bir dizinde bulacaksınız:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2. Dosyanın bir kopyasını oluşturun ve bunu **URLScan. old**olarak adlandırın.  
  
3. Urlscan.ini dosyanın özgün kopyasını Not defteri veya istediğiniz metin düzenleyicisini kullanarak açın.  
  
4. Urlscan.ini ' de [AllowVerbs] bölümünü bulun. [AllowVerbs] bölümüne hata ayıklama ekleyin. [AllowVerbs] bölümünde EBUG;D görürseniz, fiilin açıklama eklemek için noktalı virgülü kaldırın.  
  
5. [DenyVerbs] bölümünü bulun. [DenyVerbs] bölümünde hata ayıklama görüntülenirse, kaldırın.  
  
6. Dosyayı kaydedin.  
  
7. Sunucuyu yeniden başlatın veya IIS 'yi yeniden başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında hata ayıklama: hatalar ve sorun giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Hata: Web Sunucusu İstenen Kaynağı Bulamadı](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)
