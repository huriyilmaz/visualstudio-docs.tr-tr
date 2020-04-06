---
title: IDebugDocumentPositionOffset2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731603"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Kaynak dosyadaki bir konumu karakter ofset olarak temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 IDE tarafından uygulanan ve hata ayıklama motorları tarafından tüketilen.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugDocumentPositionOffset2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Geçerli belge konumunun aralığını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu, [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ile aynı `char` bilgileri döndürür, ancak belgenin başlangıcından itibaren uzaklıklarda. Bu, belgeyi normalde döndürülen satır ve sütun bilgileri yerine tek boyutlu bir karakter dizisi olan bir diskte var olacak gibi sunar.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
