---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af72993a4a02ce7d25858bf3bd4f0690e0d30f5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923098"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Bu arabirim bir metin belgesini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir hata ayıklama altyapısı (DE), sağlaması gereken kaynak kodu metin biçiminde olduğunda bu arabirimi uygular. Bu en tipik durum olduğu için, [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini de uygularsa, arabirimi de uygulamalıdır `IDebugDocumentText2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 `QueryInterface`Bu arabirimi bir arabirimden elde etmek için yöntemini kullanın `IDebugDocument2` .

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim, arabirimindeki yöntemlere ek olarak `IDebugDocument2` aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Belgedeki bu konumdaki metnin boyutunu alır.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Belgedeki belirtilen konumdan metni alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimi uygulayan bir nesne <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> , <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> bir [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) nesnesinin arabirimini sağlayan arabirimini de uygulamalıdır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
