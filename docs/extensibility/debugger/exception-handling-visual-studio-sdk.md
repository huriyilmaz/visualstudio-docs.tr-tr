---
title: Özel durum Işleme (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738767"
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

6. Hata ayıklamakta olan programın ikinci şans özel durumu için işleyici yoksa, DE `IDebugExceptionEvent2` **event_sync_stop**olarak SDM 'yi gönderir.

7. Hata ayıklama paketi kullanıcıdan bir ilk şans özel durum iletişim kutusunu açarak özel durumu nasıl işlemesini ister.

8. Hata ayıklama paketi, kullanıcıya hangi seçenekleri suntuğıi belirlemek için [IDebugExceptionEvent2:: Canpasstodebugayıklanan](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) öğesini çağırır.

9. Hata ayıklama paketi, bir ikinci şans özel durum iletişim kutusunu açarak kullanıcıya özel durumu nasıl işleyeceğinizi ister.

10. Yöntem S_OK döndürürse çağırır `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
