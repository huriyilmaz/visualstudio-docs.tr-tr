---
title: IDebugProcessQueryProperties | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723285"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Bu arabirim, [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) uygulayıcıları tarafından uygulanan bir uzantı arabirimidir. Uygulayıcının hata ayıklama işlemi ortamı hakkında bilgi almalarına olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama işleminin yürütme ortamı hakkında bilgi almak için bu arabirimi uygulayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProcessQueryProperties`.

|Yöntem|Açıklama|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Özellik değeri için sorgular.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Özellik değerleri için sorgular.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim nadiren uygulanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portpriv.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
