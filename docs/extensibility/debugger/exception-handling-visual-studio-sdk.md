---
title: Özel durum Işleme (Visual Studio SDK) | Microsoft Docs
description: Özel durumlar oluştuğunda oluşan işlem hakkında bilgi edinin. Bu makalede, ilgili tüm adımlar açıklanmaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ed8db28a7196551e2f1c8236d71e0f2291fce934
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921522"
---
# <a name="exception-handling-visual-studio-sdk"></a>Özel durum işleme (Visual Studio SDK)
Aşağıdakiler, özel durumlar oluşturulduğunda oluşan süreci açıklar.

## <a name="exception-handling-process"></a>Özel durum işleme işlemi

1. Bir özel durum ilk oluşturulduğunda, ancak hata ayıklamakta olan programdaki özel durum işleyicisi tarafından işlenemeden önce, hata ayıklama altyapısı (DE), oturum hata ayıklama Yöneticisi 'ne (SDM) durdurma olayı olarak bir [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) gönderir. `IDebugExceptionEvent2`Yalnızca özel durum ayarları (hata ayıklama paketindeki özel durumlar iletişim kutusunda belirtilir), kullanıcının birinci şans özel durum bildirimlerini durdurmak istediğini belirtmek isterse gönderilir.

2. SDM, özel durumun özelliğini almak için [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) çağırır.

3. Hata ayıklama paketi, kullanıcıya hangi seçenekleri suntuğıi belirlemek için [IDebugExceptionEvent2:: Canpasstodebugayıklanan](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) öğesini çağırır.

4. Hata ayıklama paketi kullanıcıdan bir ilk şans özel durum iletişim kutusunu açarak özel durumu nasıl işlemesini ister.

5. Kullanıcı devam etmeyi seçerse SDM, [IDebugExceptionEvent2:: Canpasstodebugayıklanan](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)öğesini çağırır.

    - Yöntem S_OK döndürürse, [IDebugExceptionEvent2::P Asstodebugayıklanan](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)çağırır.

         -veya-

         Yöntem S_FALSE döndürürse, hata ayıklamakta olan programa özel durumu işlemek için ikinci bir şans verilir.

6. Hata ayıklamakta olan programın ikinci şans özel durumu için işleyici yoksa, DE `IDebugExceptionEvent2` **event_sync_stop** olarak SDM 'yi gönderir.

7. Hata ayıklama paketi kullanıcıdan bir ilk şans özel durum iletişim kutusunu açarak özel durumu nasıl işlemesini ister.

8. Hata ayıklama paketi, kullanıcıya hangi seçenekleri suntuğıi belirlemek için [IDebugExceptionEvent2:: Canpasstodebugayıklanan](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) öğesini çağırır.

9. Hata ayıklama paketi, bir ikinci şans özel durum iletişim kutusunu açarak kullanıcıya özel durumu nasıl işleyeceğinizi ister.

10. Yöntem S_OK döndürürse çağırır `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
