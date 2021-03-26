---
description: Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini alır.
title: 'IDebugProcess3:: GetEngineFilter | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c2628424f4f5e9446c763324dfcf9ced4f1896e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076569"
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEngineFilter(
   GUID_ARRAY *pEngineArray
);
```

```csharp
public int GetEngineFilter(
   out GUID_ARRAY[] pEngineArray
);
```

## <a name="parameters"></a>Parametreler
`pEngineArray`\
dışı Hata ayıklama motorları için benzersiz tanımlayıcılar içeren bir yapıya başvuru.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)
