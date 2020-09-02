---
title: Düzenle ve devam et hata Iletisi Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428306"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Düzenle ve Devam Et Hata İletisi İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve devam et 'i destekleyen bir dilde hata ayıklarken bu iletişim kutusu görüntülenir, ancak yaptığınız kod değişikliklerinin türü için **Düzenle ve devam et** kullanılamaz. Kutu içindeki hata mesajı daha ayrıntılı bir açıklama sağlar. Bu iletişim kutusunu görmenizin olası nedenleri şunlardır:  
  
- Yönetilmeyen hata ayıklama etkinleştirildiğinde yönetilen kodu düzenlemeye çalıştınız. Düzenle ve devam et karışık modda hata ayıklama ile çalışmaz.  
  
- SQL Server kodu düzenlemeye çalıştınız.  
  
- Dr. Watson dökümünden hata ayıklarken kodu düzenlemeye çalıştınız.  
  
- İşlenmeyen bir özel durum oluştuğundan kodu düzenlemeye çalıştınız ve "**işlenmemiş özel durumlarla çağrı yığınını geriye doğru izleme**" seçeneği işaretli değil.  
  
- Gömülü çalışma zamanı uygulamasında hata ayıklarken kodu düzenlemeye çalıştınız.  
  
- **Hata ayıklama** menüsünden başlamak yerine, eklediğiniz bir programda kodu düzenlemeye çalıştınız.  
  
- İyileştirilmiş kodu düzenlemeye çalıştınız.  
  
- Hedef, 64 bitlik bir uygulama olduğunda yönetilen kodu düzenlemeye çalıştınız. Düzenle ve devam et ' i kullanmak istiyorsanız, hedefi x86 olarak ayarlamanız gerekir. (*Proje* **özellikleri**, **derleme** sekmesi, **Gelişmiş derleyici** ayarı.).  
  
- Hata ayıklama sırasında değiştirilmiş ve yeniden yüklenmiş bir derlemede kodu düzenlemeye çalıştınız.  
  
- Yüklenmemiş bir derlemede kodu düzenlemeye çalıştınız.  
  
- Uygulamanızın eski bir sürümünde hata ayıklamaya başladıysanız (yeni sürümde derleme hataları olduğundan).  
  
- Çalışırken kodu düzenlemeye çalıştınız.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Tamam**  
 İletişim kutusundan çıkın ve hemen önceki düzenleme girişimini iptal edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)
