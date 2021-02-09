---
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea8de97a82959b1135866988aeeeb14cf464e8b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925076"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Bu yöntem, programdan diğer adların bir listesini alır.

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
'ndaki Döndürülecek diğer ad sayısı üst sınırı (geçirilen dizinin uzunluğunu belirtir `ppAliases` ).

`ppAliases`\
[in, out] Diğer adlarla doldurulacak dizi (Eğer bu null bir değer ise ve `uRequest` 0 ise, döndürülebilecek diğer adların sayısı tarafından döndürülecektir `puFetched` ).

`puFetched`\
dışı Alınan diğer adların sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
