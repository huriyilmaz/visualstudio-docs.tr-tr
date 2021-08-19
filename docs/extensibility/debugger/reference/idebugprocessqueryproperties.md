---
description: Bu arabirim, IDebugProcess2 uygulayanları tarafından uygulanan bir uzantı arabirimidir.
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e71603039747356ab1f3ba68b7f8750d4e21986d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159847"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Bu arabirim, [IDebugProcess2 uygulayanları tarafından uygulanan bir uzantı](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimidir. Bu, uygulamanın hata ayıklama işlemi ortamı hakkında bilgi alamasını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama işleminin yürütme ortamı hakkında bilgi almak için bu arabirimi kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProcessQueryProperties` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Özellik değeri için sorgular.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Özellik değerleri için sorgular.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim nadiren uygulanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Portpriv.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
