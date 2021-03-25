---
description: Bu arabirim, IDebugProcess2 ımplemenbu tarafından uygulanan bir uzantı arabirimidir.
title: Idebugprocessqueryproperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5fb8766e9cd0f48e85fa0b060efb4faa7bc496
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076296"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Bu arabirim, [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) ımplemenbu tarafından uygulanan bir uzantı arabirimidir. Uygulayıcının hata ayıklama işlem ortamıyla ilgili bilgi almasına izin verir.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama sürecinin yürütme ortamıyla ilgili bilgi almak için bu arabirimi uygulayın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProcessQueryProperties` .

|Yöntem|Açıklama|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Bir özellik değeri için sorgular.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Özellik değerleri için sorgular.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim nadiren uygulanabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
