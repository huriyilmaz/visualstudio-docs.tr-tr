---
description: Bu arabirim, kaynak dosya belgesinde bir konumu temsil eder.
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b28f18061f6a0bc76ad69da6a2fc27b0d30593f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096394"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Bu arabirim, kaynak dosya belgesinde bir konumu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kaynak kodu düzeyinde hata ayıklama desteğinin bir parçası olarak bu arabirimi uygulamaya almaktadır. Bu arabirim, kaynak kodundaki bir konuma ek olarak bağlamları karşılaştırmak ve kaynak kod belgesinde gezinmek için yöntemler sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Çeşitli arabirimlerde yöntemler( genellikle [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) arabirimleri) bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugDocumentContext2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Bu belge bağlamını içeren belgeyi alır.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Bu belge bağlamını içeren belgenin görünen adını alır.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Bu belge bağlamıyla ilişkili tüm kod bağlamlarının listesini alın.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Bu belge bağlamıyla ilişkili dili alır.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Bu belge bağlamının dosya deyimi aralığını alır.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Bu belge bağlamının dosya kaynak aralığını alır.|
|[Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Bu belge bağlamını, belge bağlamlarının verilen bir dizisiyle karşılar.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Belge bağlamını, verilen sayıda deyim veya satırla taşır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
