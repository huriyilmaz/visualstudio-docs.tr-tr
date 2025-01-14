---
description: Bu yöntem, programdan diğer adların listesini alıyor.
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ab2624e21723b635d6e7db6551cb370308d43d0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627489"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Bu yöntem, programdan diğer adların listesini alıyor.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Parametreler
`uRequest`\
[in] Dönüş için en fazla diğer ad sayısı (içine geçirilen dizinin uzunluğunu `ppAliases` belirtir).

`ppAliases`\
[in, out] Diğer adlarla doldurulacak dizi (bu bir null değerse ve 0 ise, döndürülecek diğer ad `uRequest` sayısı tarafından `puFetched` döndürülür).

`puFetched`\
[out] Alınan diğer ad sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
