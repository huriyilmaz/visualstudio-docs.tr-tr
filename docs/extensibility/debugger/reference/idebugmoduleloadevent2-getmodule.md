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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4605b5eab9137fd918238143d8f0453f9f8c54b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065378"
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
