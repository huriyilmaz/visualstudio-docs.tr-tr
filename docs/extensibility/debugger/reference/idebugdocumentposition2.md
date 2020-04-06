---
title: IDebugDocumentPosition2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731644"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Bu arabirim, kaynak dosyadaki soyut bir konumu temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio genellikle bu arabirimi uygular. Hata ayıklama altyapısı (DE), kendi kaynak kodunu sağlaması gerekiyorsa (DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uyguladığı nda olduğu gibi) bu arabirimi de uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu [arabirim, EnumCodeContexts'a](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)bağımsız değişken olarak aktarılır. Ayrıca, bekleyen bir kesme noktası oluşturmada kullanılan [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapının sırayla bir parçası olan [bir BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) birliğinin (özellikle [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) bir yapının) bir parçası olarak da sağlanır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugDocumentPosition2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Bu belge konumunu içeren kaynak dosyanın dosya adını alır.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|İçeren belgeyi alır.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bu konumun verilen belgede bulununp içermeyileceğini belirler.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Bu belge konumu için aralığı alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
