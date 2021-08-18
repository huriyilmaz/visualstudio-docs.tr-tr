---
description: Kaynak dosyadaki bir konumu karakter boşluğu olarak temsil eder.
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f6fdb3fc220a4495146ad9ca66e4b2cee73f1909
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119444"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Kaynak dosyadaki bir konumu karakter boşluğu olarak temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 IDE tarafından uygulanır ve hata ayıklama motorları tarafından kullanılır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocumentPositionOffset2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Geçerli belge konumunun aralığını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu, [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ile aynı bilgileri, `char` Belgenin başından uzaklıklardan geri döndürür. Bu, belgeyi bir diskte var olduğu gibi, diğer bir deyişle, genellikle döndürülen satır ve sütun bilgileri yerine, tek boyutlu bir karakter dizisi gibi gösterir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
