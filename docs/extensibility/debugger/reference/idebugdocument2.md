---
description: Bu arabirim bir kaynak belgeyi temsil eder.
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7af2cadaa7747478a1609251d14fe1af6a518a2c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096420"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Bu arabirim bir kaynak belgeyi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] genellikle bu arabirimi uygulanır. Hata ayıklama altyapısı (DE), kaynak kodu sağlamak için gerekli olduğunda ve kaynak diskte mevcut değilken de bu arabirimi gerçekleştirebilirsiniz.  Bu gibi durumlarda DE, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) ve [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) arabirimlerini ve [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) ve [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) arabirimleri üzerinde bazı ek yöntemleri de uygulamalı.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 , , `IDebugDocumentContext2` ve `IDebugDisassemblyStream2` `IDebugDocumentPosition2` arabirimleri üzerinde `IDebugActivateDocumentEvent2` yöntemler bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugDocument2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Belgenin adını birkaç formdan birini alır.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Belgenin sınıf tanımlayıcısını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim yalnızca DE kaynak kodu sağlarken uygulanır. Örneğin, bir HTML sayfasında betikte hata ayıklaması yapıyorsanız, kaynak dinamik olarak indirilir veya oluşturulur ve disk dosyası olarak mevcut değildir. C++ gibi geleneksel dillerde hata ayıklarken bu arabirimin uygulanmasına gerek yok.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
