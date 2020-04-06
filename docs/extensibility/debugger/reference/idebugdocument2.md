---
title: IDebugDocument2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731993"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Bu arabirim bir kaynak belgeyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]genellikle bu arabirimi uygular. Hata ayıklama altyapısı (DE), kaynak kodu sağlaması gerektiğinde ve kaynak diskte yokolduğunda bu arabirimi de uygulayabilir.  Bu gibi durumlarda, DE ayrıca [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) ve [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) arabirimlerinin yanı sıra [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) ve [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) arabirimlerinde bazı ek yöntemler uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 `IDebugDocumentContext2`, , `IDebugDisassemblyStream2` `IDebugDocumentPosition2`ve `IDebugActivateDocumentEvent2` arabirimlerdeki yöntemler bu arabirimi döndürer.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugDocument2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Belgenin adını çeşitli formlardan birinde alır.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Belgenin sınıf tanımlayıcısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim yalnızca DE kaynak kodu sağladığında uygulanır. Örneğin, bir HTML sayfasında komut dosyası nın hata ayıklama hizmetindeyken, kaynak karşıdan yüklendiğinden veya dinamik olarak oluşturulduğundan ve disk dosyası olarak bulunmadığından DE kaynak kodunu sağlar. C++ gibi geleneksel dilleri hata ayıklarken, bu arabirimin uygulanması gerekmez.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
