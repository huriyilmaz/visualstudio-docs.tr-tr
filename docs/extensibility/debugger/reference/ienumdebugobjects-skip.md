---
description: Bu yöntem, belirtilen sayıda IDebugObject öğesi üzerinde atlar.
title: 'IEnumDebugObjects:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 962083242b5b178ddf39e21328917d09dc0ed09a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224648"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Bu yöntem, belirtilen sayıda öğeyi atlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Parametreler
`celt`\
'ndaki Atlanacak öğe sayısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE` `celt` Kalan öğelerin sayısından büyükse döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `celt`Kalan öğelerin sayısından daha büyük bir değer belirtiyorsa, numaralandırma sonuna ayarlanır ve `S_FALSE` döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
