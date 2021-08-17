---
description: Bu arabirim bir metin belgesini temsil eder.
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ffb2aa817caff01b598bc789c6aaa8b7dbacfcd1d3d590a7715f6be4e18d1121
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417346"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Bu arabirim bir metin belgesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir hata ayıklama altyapısı (DE), kaynağı olması gereken kaynak kod metin formunda olduğunda bu arabirimi uygulamaz. Bu en tipik durum olduğu için, DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uygulayıyorsa arabirimini de uygulaması `IDebugDocumentText2` gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `QueryInterface` bir arabirimden almak için yöntemini `IDebugDocument2` kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Bu arabirim, arabirimde `IDebugDocument2` yöntemlerine ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Belgenin bu konumundaki metnin boyutunu alın.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Belgede belirtilen konumdan metni alan.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimi uygulayan bir nesne, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) nesnesi için arabirimini sağlar arabirimini de uygulamalı.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
