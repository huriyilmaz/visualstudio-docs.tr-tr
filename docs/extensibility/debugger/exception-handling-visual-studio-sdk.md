---
title: Özel Durum Taşıma (Visual Studio SDK) | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738767"
---
# <a name="exception-handling-visual-studio-sdk"></a>Özel durum işleme (Visual Studio SDK)
İstisnalar atıldığında oluşan işlem aşağıda açıklanır.

## <a name="exception-handling-process"></a>Özel durum işleme işlemi

1. Bir özel durum ilk atıldığında, ancak programda özel durum işleyicisi tarafından işlenmeden önce hata ayıklama altyapısı (DE) bir [iDebugExceptionEvent2'yi](../../extensibility/debugger/reference/idebugexceptionevent2.md) durdurma olayı olarak oturum hata ayıklama yöneticisine (SDM) gönderir. Yalnızca `IDebugExceptionEvent2` özel durum ayarları (hata ayıklama paketindeki Özel Durumlar iletişim kutusunda belirtilmişse) kullanıcının ilk şans özel durum bildirimlerinde durdurmak istediğini belirtse gönderilir.

2. SDM, özel durum özelliğini almak için [IDebugExceptionEvent2::GetException'ı](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) çağırır.

3. Hata ayıklama paketi [iDebugExceptionEvent2 çağırır::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) hangi seçenekleri kullanıcıya sunmak için belirlemek için.

4. Hata ayıklama paketi, ilk şans özel durum iletişim kutusunu açarak kullanıcıya özel durumu nasıl işleyeceğini sorar.

5. Kullanıcı devam etmeyi seçerse, SDM [IDebugExceptionEvent2 çağırır::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Yöntem S_OK döndürürse, [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)çağırır.

         -veya-

         Yöntem S_FALSE döndürürse, debugged olan program özel durumu işlemek için ikinci bir şans verilir.

6. Debugged olan program ikinci bir şans özel durum için hiçbir `IDebugExceptionEvent2` işleyicisi varsa, DE **EVENT_SYNC_STOP**olarak SDM bir gönderir.

7. Hata ayıklama paketi, ilk şans özel durum iletişim kutusunu açarak kullanıcıya özel durumu nasıl işleyeceğini sorar.

8. Hata ayıklama paketi [iDebugExceptionEvent2 çağırır::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) hangi seçenekleri kullanıcıya sunmak için belirlemek için.

9. Hata ayıklama paketi, ikinci şans özel durum iletişim kutusunu açarak kullanıcıya özel durumu nasıl işleyeceğini sorar.

10. Yöntem S_OK dönerse, `IDebugExceptionEvent2::PassToDebuggee`çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını arama](../../extensibility/debugger/calling-debugger-events.md)
