---
description: Bu arabirim, kaynak dosyadaki bir soyut konumu temsil eder.
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 56e809bdc8b6cb8d22fc89cd216f9e8920dc4359
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634969"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Bu arabirim, kaynak dosyadaki bir soyut konumu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio genellikle bu arabirimi uygular. Bir hata ayıklama altyapısı (DE), aynı zamanda kendi kaynak kodunu sağlaması gerekiyorsa ( [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uyguluyorsa olduğu gibi) bu arabirimi de uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, [Enumcodebağlamları](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)için bir bağımsız değişken olarak geçirilir. Ayrıca, bekleyen bir kesme noktası oluşturmak için kullanılan [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapısının parçası olan bir [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) birleşimin (özellikle de bir [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) yapısı) bir parçası olarak da sağlanır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocumentPosition2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Bu belge konumunu içeren kaynak dosyanın dosya adını alır.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|İçeren belgeyi alır.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bu konumun verilen belgede içerildiğini belirler.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Bu belge konumunun aralığını alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
