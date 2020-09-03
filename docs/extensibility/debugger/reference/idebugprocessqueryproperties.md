---
title: Idebugprocessqueryproperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723285"
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
