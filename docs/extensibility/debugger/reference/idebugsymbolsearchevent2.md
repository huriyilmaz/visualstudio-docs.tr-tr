---
description: Bu arabirim, hata ayıklama altyapısı (DE) tarafından, hata ayıklamakta olan bir modülün hata ayıklama simgelerinin yüklendiğini göstermek için gönderilir.
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
ms.openlocfilehash: d61bcc7c77295b59bc6cc66cd1cf9aac3486e6c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103656"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Bu arabirim, hata ayıklama altyapısı (DE) tarafından, hata ayıklamakta olan bir modülün hata ayıklama simgelerinin yüklendiğini göstermek için gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, bir modülün simgelerinin yüklendiğini raporlamak için DE bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir modülün simgelerinin yüklendiğini raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 `IDebugSymbolSearchEvent2`Arabirimi aşağıdaki yöntemi sunar.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Bir sembol aramasının sonuçları hakkındaki bilgileri alır.|

## <a name="remarks"></a>Açıklamalar
 Simgeler yüklenemese de bu olay gönderilir. Çağırmak, `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` modülün gerçekten bir simgelere sahip olup olmadığını belirlemede bu olayın işleyicisine izin verir.

 Visual Studio, genellikle bu olayı **modüller** penceresindeki yüklü simgelerin durumunu güncelleştirmek için kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
