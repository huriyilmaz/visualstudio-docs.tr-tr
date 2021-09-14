---
description: Dizide tanımlanmış temel dizinler (alt sınırlar) olup olmadığını belirler.
title: 'IDebugArrayObject2:: Hasbasedizinler | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7f722a5f54674d64a9dccb79b03b1025cc4824
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627548"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Dizide tanımlanmış temel dizinler (alt sınırlar) olup olmadığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT HasBaseIndices (
   BOOL* pfHasBaseIndices
);
```

```csharp
int HasBaseIndices (
   out bool pfHasBaseIndices
);
```

## <a name="parameters"></a>Parametreler
`pfHasBaseIndices`\
dışı Dizinin temel dizin (alt sınır) olduğunu belirtmek için TRUE. Aksi takdirde, FALSE.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.
