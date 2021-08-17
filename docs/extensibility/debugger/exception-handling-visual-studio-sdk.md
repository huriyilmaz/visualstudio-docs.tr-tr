---
title: Özel Durum İşleme (Visual Studio SDK) | Microsoft Docs
description: Özel durumlar oluştuğunda oluşan işlem hakkında bilgi edinmek. Bu makalede ilgili tüm adımlar açıklanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3763c38fa99f28ac2af52ef821aac2c623720b4c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096628"
---
# <a name="exception-handling-visual-studio-sdk"></a>Özel durum işleme (Visual Studio SDK)
Aşağıda, özel durumlar oluştuğunda oluşan işlem açıkmektedir.

## <a name="exception-handling-process"></a>Özel durum işleme işlemi

1. Bir özel durum ilk kez sızıp hata ayıklanılan programda özel durum işleyicisi tarafından işlendi olmadan önce, hata ayıklama altyapısı (DE), oturum hata ayıklama yöneticisine (SDM) bir durdurma olayı olarak [bir IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) gönderir. yalnızca özel durum ayarları (hata ayıklama paketinde Özel Durumlar iletişim kutusunda belirtilir) kullanıcının ilk şans özel durum bildirimlerini durdurmak istediğini `IDebugExceptionEvent2` belirtirse gönderilir.

2. SDM, özel durumun özelliğini almak için [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) çağrısında bulundu.

3. Hata ayıklama paketi, kullanıcıya sunacak seçenekleri belirlemek için [IDebugExceptionEvent2::CanPassToDebuggee'yi](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) arar.

4. Hata ayıklama paketi, kullanıcıya birinci şans özel durum iletişim kutusunu açarak özel durumu nasıl işley olduğunu sorar.

5. Kullanıcı devam etmek seçerse, SDM [IDebugExceptionEvent2::CanPassToDebuggee'yi arar.](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)

    - Yöntem bir S_OK döndürürse, [IDebugExceptionEvent2::P assToDebuggee'yi arar.](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)

         -veya-

         Yöntem bir S_FALSE döndürürse, hata ayıklaması yapılan programa özel durumu işlemesi için ikinci bir şans verilir.

6. Hata ayıklaması yapılan programın ikinci şans özel durumu için işleyicisi yoksa, DE `IDebugExceptionEvent2` SDM'ye bir EVENT_SYNC_STOP. 

7. Hata ayıklama paketi, kullanıcıya birinci şans özel durum iletişim kutusunu açarak özel durumu nasıl işley olduğunu sorar.

8. Hata ayıklama paketi, kullanıcıya sunacak seçenekleri belirlemek için [IDebugExceptionEvent2::CanPassToDebuggee'yi](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) arar.

9. Hata ayıklama paketi kullanıcıya ikinci bir özel durum iletişim kutusu açarak özel durumu nasıl işley olduğunu sorar.

10. Yöntem bir S_OK `IDebugExceptionEvent2::PassToDebuggee` çağıran.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
