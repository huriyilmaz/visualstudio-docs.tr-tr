---
title: Microsoft Visual Studio Hata ayıklayıcı (özel durum oluştu) Iletişim kutusu | Microsoft Docs
titleSuffix: ''
description: 'Programınızın işlenmesi gereken bir özel durum oluştuğunda ne yapılacağını öğrenin. Şunları yapabilirsiniz: 1) hata ayıklayıcıya kesme; 2) devam et; veya 3) yoksay.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 674c54be9ecf2fbe2cc2740275da0bc57cff9c17
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971588"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Hata Ayıklayıcısı (Özel Durum Oluştu) İletişim Kutusu
Programınızda bir özel durum oluştu. Bu iletişim kutusu oluşturulan özel durum türünü bildirir. Kodunuzun bu özel durumu işlemesi gerekiyor. Özel durumu işlemek için aşağıdaki seçenekler arasından seçim yapabilirsiniz:

 **Kes** Yürütmenin hata ayıklayıcıya kesilmesine izin verir. Özel durum işleyicisi, break öncesinde çağrılmaz. Kesmeyi devam ederseniz, özel durum işleyicisi çağrılır.

 **Devam et** Yürütmenin devam etmesine izin vererek özel durum işleyicisine özel durumu işleme şansı verir. Bu seçenek belirli özel durum türleri için kullanılamaz. **Devam et** , uygulamanın devam etmesine izin verir. Yerel bir uygulamada, özel durumun yeniden oluşturulmasına neden olur. Yönetilen bir uygulamada, programın sonlanmasına veya bir barındırma uygulaması tarafından işlenmesi için özel duruma neden olur.

> [!NOTE]
> Yönetilen kodda işlenmeyen bir özel durumla sonra devam edemezsiniz. Yönetilen koddaki işlenmeyen bir özel durum, hata **ayıklamanın durdurulmasına** neden olur.

 **Yoksay** Yürütmenin özel durum işleyicisini çağırmadan devam etmesine izin verir. Özel durum işleyicisi çağrılamadığından, ek özel durumlar ve hatalar da dahil olmak üzere daha fazla sonuçlara yol açabilir. Bu seçenek belirli özel durum türleri için kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
- [Özel Durumlar için En İyi Yöntemler](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Özel Durum İşleme](/cpp/extensions/exception-handling-cpp-component-extensions)