---
description: Modüller numaralandırmasındaki sonraki öğe kümesini döndürür.
title: 'IEnumDebugModules2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7c1d627579faea8bb4871feb310db79d6e5eea0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226403"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Numaralandırmadaki öğelerin bir sonraki kümesini döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`celt`\
'ndaki Alınacak öğe sayısı. Ayrıca, dizinin en büyük boyutunu belirtir `rgelt` .

`rgelt`\
[in, out] Doldurulacak [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) öğelerinin dizisi.

`pceltFetched`\
dışı İçinde gerçekten döndürülen öğelerin sayısını döndürür `rgelt` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`İstenen sayıda öğeden daha az döndürülüp döndürülmeyeceğini döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
