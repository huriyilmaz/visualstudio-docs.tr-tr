---
title: Web sunucusu kilitlenmiş ve hata ayıklama fiilini engelliyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e68ab09d7fc398d45a8942c3df4ca0dee5754d2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871220"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor
Web uygulamasına veya XML Web hizmetine adımlamak, IIS Kilitleme Aracı çalıştırıldığı ve URLScan yüklenmiş ve etkinleştirilmiş olduğundan başarısız oldu. Bu koşul, IIS 'nin hata ayıklama fiilini almasını engeller.

 URLScan, IIS Web sitesi yöneticilerine gereksiz özellikleri kapatma ve sunucunun işleyeceğini HTTP isteklerinin türünü kısıtlama yeteneği sağlamak için IIS kilitleme aracı ile birlikte çalışan bir güvenlik aracıdır. URLScan güvenlik aracı, belirli HTTP isteklerini engelleyerek, zararlı olabilecek isteklerin sunucuya ulaşmasını ve hasar vermesine neden olur.

 Uygulamanız Windows Server 2003 üzerinde IIS 6,0 üzerinde çalışıyorsa, IIS 6,0 aynı işlevselliği sağladığından IIS Kilitleme Aracı 'nı çalıştırmanız gerekir.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>URLScan yüklü bir Web sunucusunda hata ayıklamayı etkinleştirmek için

1. Urlscan.ini dosyasını bulun. Normalde, bunu şuna benzer bir dizinde bulacaksınız:

     C:\WINNT\System32\Inetsrv\urlscan

2. Dosyanın bir kopyasını oluşturun ve bunu **URLScan. old** olarak adlandırın.

3. Urlscan.ini dosyanın özgün kopyasını Not defteri veya istediğiniz metin düzenleyicisini kullanarak açın.

4. Urlscan.ini ' de [AllowVerbs] bölümünü bulun. [AllowVerbs] bölümüne hata ayıklama ekleyin. [AllowVerbs] bölümünde EBUG;D görürseniz, fiilin açıklama eklemek için noktalı virgülü kaldırın.

5. [DenyVerbs] bölümünü bulun. [DenyVerbs] bölümünde hata ayıklama görüntülenirse, kaldırın.

6. Dosyayı kaydedin.

7. Sunucuyu yeniden başlatın veya IIS 'yi yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Hata: Web Sunucusu İstenen Kaynağı Bulamadı](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)