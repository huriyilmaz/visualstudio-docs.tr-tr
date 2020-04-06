---
title: IDebugDocumentText2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731567"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Bu arabirim bir metin belgesini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), sağlaması gereken kaynak kodu metin biçiminde olduğunda bu arabirimi uygular. Bu en tipik durum olduğundan, bir DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uygularsa, `IDebugDocumentText2` arabirimi de uygulamalıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu `QueryInterface` arabirimi bir `IDebugDocument2` arabirimden elde etmek için yöntemi kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 `IDebugDocument2` Arabirimdeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Belgedeki bu konumdaki metnin boyutunu alır.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Belgedeki belirtilen konumdan metni alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimi uygulayan bir nesne, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> bir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) nesnesi için arabirimi sağlayan arabirimi de uygulamalıdır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
