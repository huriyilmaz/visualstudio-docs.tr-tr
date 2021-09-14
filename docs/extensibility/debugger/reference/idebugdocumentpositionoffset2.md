---
description: Kaynak dosyada bir konumu karakter uzaklığı olarak temsil eder.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634953"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Kaynak dosyada bir konumu karakter uzaklığı olarak temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 IDE tarafından uygulanır ve hata ayıklama altyapıları tarafından tüketilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugDocumentPositionOffset2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Geçerli belge konumunun aralığını alın.|

## <a name="remarks"></a>Açıklamalar
 Bu, [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) ile aynı bilgileri ancak `char` belgenin başından itibaren uzaklıklar olarak döndürür. Bu, belgeyi bir diskte var olduğu gibi, yani normalde döndürülen satır ve sütun bilgileri yerine tek boyutlu bir karakter dizisi olarak sunar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
