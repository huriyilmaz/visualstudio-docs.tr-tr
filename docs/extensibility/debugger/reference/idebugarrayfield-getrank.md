---
description: Dizinin boyutlarının derecesini veya sayısını alır.
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a35563f55824ae95269c944f34f87a8af2222a08
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627596"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Dizinin boyutlarının derecesini veya sayısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametreler
`pdwRank`\
[out] Dereceyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir dizinin derecesi boyut sayısına karşılık gelen bir değerdir. C++ ve C# içinde çok boyutlu diziler aslında dizi dizileridir ve bu nedenle yalnızca tek boyutlu bir dizi olarak kabul edilir (ve yöntem her zaman `GetRank` 1 döndürür). 'de ise, çok boyutlu diziler farklı şekilde iş alır ve böyle bir dizinin sıralaması boyut sayısını gösterir (ve yöntem her zaman boyut [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] `GetRank` sayısını döndürür).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
