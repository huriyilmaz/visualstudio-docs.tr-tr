---
description: Kaynak Sunucu kullanırken bu uyarı iletişim kutusu görüntülenir.
title: 'Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dce19c368cc1130a2f06da6b9c656fad529b3728
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636630"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli
Kaynak Sunucu kullanırken bu uyarı iletişim kutusu görüntülenir. Hata ayıklayıcının kaynak kodu almak için yürütmesi gereken komutun, kaynak dosyada yer alan Kaynak Sunucu için güvenilir komutlar listesinde srcsvr.ini gösterir. Bu geçerli bir komutsa, bu komutu srcsvr.ini ebilirsiniz. Aksi takdirde çalıştırmamalısınız. Daha fazla bilgi için [bkz. Sembol Belirtme (.pdb) ve Kaynak Dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="message-text"></a>İleti Metni
 **Kaynak sunucudan kaynak kodu almak için hata ayıklayıcı aşağıdaki güvenilmeyen komutu yürütmalıdır.**

 **Hata ayıklama sembol dosyası ( .pdb) bilinen ve güvenilen bir kaynaktan yoksa, bu komut geçersiz veya çalıştırmak \* tehlikeli olabilir.**

 **Bu komutu çalıştırmak istiyor musunuz?**

## <a name="uielement-list"></a>UIElement Listesi
 Çalıştıracak .pdb dosyasından Text Box Komutu.

 Komutun çalışmasına izin ver'i çalıştırın.

 Komutun yürütülmesini durdurmayı ve dosyayı Kaynak Sunucu'dan indirmeyi Çalıştır'a gerek yok.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Kaynak Sunucu](/windows/desktop/Debug/source-server-and-source-indexing)
