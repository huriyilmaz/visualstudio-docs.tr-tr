---
title: 'Güvenlik Uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683294"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak sunucu kullanırken bu uyarı iletişim kutusu görüntülenir. Hata ayıklayıcının kaynak kodu almak için yürütmesi gereken komutun, srcsvr.ini dosyasında bulunan kaynak sunucu için güvenilir Komutlar listesinde olmaması gerektiğini gösterir. Bu geçerli bir komut ise, srcsvr.ini dosyasına ekleyebilirsiniz. Aksi takdirde, bunu çalıştırmamalıdır. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>İleti metni  
 **Hata ayıklayıcı kaynak sunucudan kaynak kodu almak için aşağıdaki güvenilmeyen komutu yürütmelidir.**  
  
 **Hata ayıklama sembol dosyası ( \* . pdb) bilinen ve güvenilir bir kaynaktan değilse, bu komut geçersiz veya çalıştırılmak üzere tehlikeli olabilir.**  
  
 **Bu komutu çalıştırmak istiyor musunuz?**  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Metin Kutusu  
 Çalıştırmak için. pdb dosyasından komutunu çalıştırın.  
  
 Çalıştır  
 Komutun çalışmasına izin verin.  
  
 Çalıştırma  
 Komutun yürütülmesini ve kaynak sunucudan dosyayı indirmeyi durdurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Kaynak sunucu](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
