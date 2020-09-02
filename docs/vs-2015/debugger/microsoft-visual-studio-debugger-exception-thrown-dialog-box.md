---
title: Microsoft Visual Studio hata ayıklayıcı (özel durum oluştu) Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9062b1f3811b0b2b596cfb7fa016bca00143f332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66261063"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Hata Ayıklayıcısı (Özel Durum Oluştu) İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınızda bir özel durum oluştu. Bu iletişim kutusu oluşturulan özel durum türünü bildirir. Kodunuzun bu özel durumu işlemesi gerekiyor. Özel durumu işlemek için aşağıdaki seçenekler arasından seçim yapabilirsiniz:  
  
 **Sonundan**  
 Yürütmenin hata ayıklayıcıya kesilmesine izin verir. Özel durum işleyicisi, break öncesinde çağrılmaz. Kesmeyi devam ederseniz, özel durum işleyicisi çağrılır.  
  
 **Devam et**  
 Yürütmenin devam etmesine izin vererek özel durum işleyicisine özel durumu işleme şansı verir. Bu seçenek belirli özel durum türleri için kullanılamaz. **Devam et** , uygulamanın devam etmesine izin verir. Yerel bir uygulamada, özel durumun yeniden oluşturulmasına neden olur. Yönetilen bir uygulamada, programın sonlanmasına veya bir barındırma uygulaması tarafından işlenmesi için özel duruma neden olur.  
  
> [!NOTE]
> Yönetilen kodda işlenmeyen bir özel durumla sonra devam edemezsiniz. Yönetilen koddaki işlenmeyen bir özel durum, hata **ayıklamanın durdurulmasına** neden olur.  
  
 **Yoksayma**  
 Yürütmenin özel durum işleyicisini çağırmadan devam etmesine izin verir. Özel durum işleyicisi çağrılamadığından, ek özel durumlar ve hatalar da dahil olmak üzere daha fazla sonuçlara yol açabilir. Bu seçenek belirli özel durum türleri için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md)   
 [Özel durumlar için en iyi uygulamalar](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Özel Durum İşleme](/cpp/extensions/exception-handling-cpp-component-extensions)
