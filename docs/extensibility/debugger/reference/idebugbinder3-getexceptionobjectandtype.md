---
description: Bu yöntem, varsa bir nesnesiyle ilişkili özel durumu alır.
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bc0ba86c14d3257452d45f830953235a9ca09fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627483"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Bu yöntem, varsa bir nesnesiyle ilişkili özel durumu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parametreler
`ppException`\
[out] Özel durumu temsil eden nesneyi döndürür.

`ppField`\
[out] Özel durumuna neden olan belirli bir alanı temsil eden nesneyi döndürür (bu bir null değer olabilir).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

> [!NOTE]
> Bir özel durum olup olmadığını doğrulamak için tarafından döndürülen değeri kontrol `ppException` edin: null değerse, bu nesneyle ilişkilendirilmiş bir özel durum yoktur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
