---
description: Dizideki boyutların sayısını verilen her bir dizin için temel dizinleri (alt sınır) alır.
title: 'IDebugArrayObject2:: Getbasedizinler | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 584b0f39bd9f50b68f928cdfb2b93e6e9ea0af28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079941"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Dizideki boyutların sayısını verilen her bir dizin için temel dizinleri (alt sınır) alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Parametreler
`dwRank`\
'ndaki Dizinin boyut (derece) sayısı.

`dwIndices`\
dışı Dizi için temel dizinler (alt sınırlar).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örnek olarak, bu işlev aşağıdaki C# kodu tarafından oluşturulan dizi için ' 5 ' döndürür:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
