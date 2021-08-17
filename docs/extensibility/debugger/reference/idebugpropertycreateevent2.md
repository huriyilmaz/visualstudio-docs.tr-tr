---
description: Bu arabirim, belirli bir belgeyle ilişkili bir özellik oluşturduğunda hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 124f404ef5c43bd09ec4cab4489a5709dfb7f0d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071262"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Bu arabirim, belirli bir belgeyle ilişkili bir özellik oluşturduğunda hata ayıklama altyapısı (DE) tarafından oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu, bir özelliğin oluşturulduğunu raporlamak için DE bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` . Bu arabirim, yüklenmiş veya oluşturulmuş bir komut dosyasıyla ilişkili bir özellik oluşturulduysa ve bu betiğin IDE 'de görünmesi gerekiyorsa uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Aynı şekilde, bir özelliğin oluşturulduğunu raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, ayıklanmakta olan programa eklendiği zaman SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda arabirimin yöntemi gösterilmektedir `IDebugPropertyCreateEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Yeni özelliği alır.|

## <a name="remarks"></a>Açıklamalar
 Bir özelliğe ilişkili belirli bir belge veya komut dosyası varsa, bu olayı belgenin adıyla birlikte **betik belgeleri** penceresini GÜNCELLEŞTIRMEK için SDM 'ye gönderebilir. SDM, [](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) `guidDocument` bir `VARIANT` [IUnknown](/cpp/atl/iunknown) göstergesi içeren bir alma Işlemi için geıda deınfo öğesini bağımsız değişkenle çağırır. SDM, **betik belgeleri** penceresini güncelleştirmek Için kullanılan [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini almak Için bu işaretçi üzerinde [QueryInterface](/cpp/atl/queryinterface) 'i çağırır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
