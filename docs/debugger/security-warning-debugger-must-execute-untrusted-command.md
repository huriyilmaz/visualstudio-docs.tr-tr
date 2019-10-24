---
title: 'Güvenlik Uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0922461c4ca5366e6d1dc215f5711f5566d00ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729744"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli
Kaynak sunucu kullanırken bu uyarı iletişim kutusu görüntülenir. Hata ayıklayıcının kaynak kodu almak için yürütmesi gereken komutun srcsvr. ini dosyasında yer alan kaynak sunucu için güvenilir Komutlar listesinde olmadığını gösterir. Bu geçerli bir komut ise, bunu srcsvr. ini dosyasına ekleyebilirsiniz. Aksi takdirde, bunu çalıştırmamalıdır. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>İleti metni
 **Hata ayıklayıcı kaynak sunucudan kaynak kodu almak için aşağıdaki güvenilmeyen komutu yürütmelidir.**

 **Hata ayıklama sembol dosyası (\*. pdb) bilinen ve güvenilir bir kaynaktan değilse, bu komut geçersiz veya çalıştırılmak üzere tehlikeli olabilir.**

 **Bu komutu çalıştırmak istiyor musunuz?**

## <a name="uielement-list"></a>UIElement Listesi
 . Pdb dosyasından çalıştırılacak metin kutusu komutu.

 Komutun çalışmasına Izin ver ' i çalıştırın.

 Komutun yürütülmesini Durdur ve kaynak sunucudan dosyayı karşıdan yükleme işlemi çalıştırılmadı.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Kaynak sunucu](/windows/desktop/Debug/source-server-and-source-indexing)