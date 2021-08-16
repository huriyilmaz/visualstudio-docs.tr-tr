---
description: Bu yöntem, hata ayıklama altyapısına JustMyCode durum bilgilerini söyler.
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb528d3f8c12e21f327b168a88d4df070e2863188fcc8e1580135db9685c1ca4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307784"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Bu yöntem, hata ayıklama altyapısına JustMyCode durum bilgilerini söyler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametreler
`fUpdate`\
[in] Tüm bilgileri sıfırlamak için sıfır ( ) geçerli bilgileri güncelleştirmek için sıfır ( ) olmayan `TRUE` `FALSE` (önceden ayarlanmış herhangi bir şeyi yoksayarak).

`dwModules`\
[in] içinde bilgi yapısı sayısı `rgJMCSpec.`

`rgJMCSpec`\
[in] Kullanabileceğiniz [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) yapı dizisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="remarks"></a>Açıklamalar
 JustMyCode, yalnızca bir kullanıcıya ait olan kodda hata ayıklama ve sistem kodu gibi tüm ara kodları yoksayma kavramıdır( kaynak kodu söz konusu sistem kodu için kullanılabilir olsa bile).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
