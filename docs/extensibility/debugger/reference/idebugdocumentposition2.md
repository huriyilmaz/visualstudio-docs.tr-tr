---
description: Bu arabirim, kaynak dosyada soyut bir konumu temsil eder.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119457"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Bu arabirim, kaynak dosyada soyut bir konumu temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio genellikle bu arabirimi uygulamaz. Bir hata ayıklama altyapısı (DE), kendi kaynak kodunu [(DE'nin IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) arabirimini uygulaması gibi) gerektirse de bu arabirimi uygulamaya alır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, [EnumCodeContexts'e bağımsız değişken olarak geçirildi.](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) Ayrıca bekleyen kesme noktası [oluşturmada kullanılan BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısının bir [parçası olan](../../../extensibility/debugger/reference/bp-location-code-file-line.md) BP_LOCATION (özellikle BP_LOCATION_CODE_FILE_LINE yapısı) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) bir parçası olarak sağlanır.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugDocumentPosition2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Bu belge konumunu içeren kaynak dosyanın dosya adını alır.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|İçeren belgeyi alır.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bu konumun verilen belgede olup olmadığını belirler.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Bu belge konumu için aralığı alır.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
