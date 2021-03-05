---
description: Yüklenmekte olan veya bellekten kaldırılan modülü alır.
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e44268dcf4ab79e99bd1bdf5a996ae18762e139
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149840"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Yüklenmekte olan veya bellekten kaldırılan modülü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parametreler
`pModule`\
dışı Yükleme veya kaldırma işlemi olan modülü temsil eden bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi döndürür.

`pbstrDebugMessage`\
[in, out] Bu olayı açıklayan isteğe bağlı bir ileti döndürür. Bu parametre null bir değer ise, herhangi bir ileti istenmez.

`pbLoad`\
[in, out] Modül `TRUE` yüklüyorsanız sıfır ( `FALSE` ) ve modül boşaltılıyor. Bu parametre null bir değer ise, herhangi bir durum istenmez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
