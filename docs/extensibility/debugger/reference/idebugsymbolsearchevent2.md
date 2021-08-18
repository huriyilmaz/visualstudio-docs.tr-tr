---
description: Bu arabirim hata ayıklama altyapısı (DE) tarafından hata ayıklama yapılan modüle ait hata ayıklama sembollerinin yükleniyor olduğunu belirtmek için gönderilir.
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8ad39e2f9bdd08f4d6af13308635f54167c746a830c331d022a9d93b6b9170c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448747"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Bu arabirim hata ayıklama altyapısı (DE) tarafından hata ayıklama yapılan modüle ait hata ayıklama sembollerinin yükleniyor olduğunu belirtmek için gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir modülün simgelerinin yükleniyor olduğunu rapor etmek için bu arabirimini uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu olay nesnesini oluşturur ve modül sembollerinin yükleniyor olduğunu rapor etmek için gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Arabirimi `IDebugSymbolSearchEvent2` aşağıdaki yöntemi gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Bir sembol aramanın sonuçlarıyla ilgili bilgileri verir.|

## <a name="remarks"></a>Açıklamalar
 Semboller yüklenene kadar bu olay gönderilir. çağrısı, `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` modülün gerçekten herhangi bir sembole sahip olup olmadığını belirlemek için bu olayın işleyicisini sağlar.

 Visual Studio modüller penceresinde yüklenen simgelerin durumunu güncelleştirmek için genellikle **bu olayı** kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
