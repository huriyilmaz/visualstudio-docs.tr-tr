---
title: IDebugDocumentContext2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731738"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Bu arabirim, kaynak dosya belgesindeki bir konumu temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kaynak kodu düzeyi hata ayıklama desteğinin bir parçası olarak bu arabirimi uygular. Bu arabirim, kaynak kodundaki bir konuma ek olarak bağlamları karşılaştırma ve kaynak kodu belgesinde gezinme yöntemleri sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Genellikle [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) arabirimleri olmak üzere çeşitli arabirimlerdeki yöntemler bu arabirimi döndürün.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugDocumentContext2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Bu belge bağlamını içeren belgeyi alır.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Bu belge bağlamını içeren belgenin görüntülenebilir adını alır.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Bu belge bağlamıyla ilişkili tüm kod bağlamlarının listesini alır.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Bu belge bağlamıyla ilişkili dili alır.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Bu belge bağlamının dosya ekstre aralığını alır.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Bu belge bağlamının dosya kaynak aralığını alır.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Bu belge bağlamını belirli bir belge bağlamı dizisiyle karşılaştırır.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Belge bağlamını belirli sayıda deyim veya satıra göre taşır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
