---
description: IIS kilitleme aracı çalıştırıldı ve URLScan yükleyip etkinleştirildiğinden bir Web uygulamasına veya XML Web hizmetine adımlama başarısız oldu.
title: Web Sunucusu Kilitlendi ve DEBUG FiiliNi Engelliyor | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c8bcf18ea7c86036061c117beed07ecd9563525
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139089"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Hata: Web Sunucusu Kilitli ve DEBUG Fiilini Engelliyor
IIS kilitleme aracı çalıştırıldı ve URLScan yükleyip etkinleştirildiğinden bir Web uygulamasına veya XML Web hizmetine adımlama başarısız oldu. Bu koşul, IIS'nin DEBUG fiilini almalarını engeller.

 URLScan, IIS Web sitesi yöneticilerine gereksiz özellikleri kapatma ve sunucunun işleyiştirecek HTTP isteklerinin türünü kısıtlama yeteneği vermek için IIS Kilitleme Aracı ile birlikte çalışan bir güvenlik aracıdır. URLScan güvenlik aracı, belirli HTTP isteklerini engelleyerek zararlı olabilecek isteklerin sunucuya ulaşmasını ve zarara neden olma ihtimalini önler.

 Uygulamanız Windows Server 2003'te IIS 6.0 üzerinde çalışıyorsa, IIS 6.0 aynı işlevselliği sağladığı için IIS Kilitleme aracını çalıştırmanız gerekir.

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>URLScan yüklü bir Web sunucusunda hata ayıklamayı etkinleştirmek için

1. Urlscan.ini bulun. Normalde, bunu şu şekilde görünen bir dizinde bulabilirsiniz:

     C:\WINNT\System32\Inetsrv\urlscan

2. Dosyanın bir kopyasını oluşturun ve **Urlscan.old olarak ad girin.**

3. Dosyanın özgün kopyasını Urlscan.ini veya Not Defteri düzenleyiciyi kullanarak açın.

4. Bu Urlscan.ini [AllowVerbs] bölümünü bulun. [AllowVerbs] bölümüne DEBUG ekleyin. [AllowVerbs] bölümünde ;D EBUG ifadesini görüyorsanız, fiilin yorumlarını kaldırmak için noktalı virgülü kaldırın.

5. [DenyVerbs] bölümünü bulun. [DenyVerbs] bölümünde DEBUG görünüyorsa kaldırın.

6. Dosyayı kaydedin.

7. Sunucuyu yeniden başlatın veya IIS'yi yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Hata: Web Sunucusu İstenen Kaynağı Bulamadı](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)
