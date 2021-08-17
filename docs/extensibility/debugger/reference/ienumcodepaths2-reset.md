---
description: Kod yolları numaralamalarını ilk öğeye sıfırlar.
title: IEnumCodePaths2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 909f85f64dd9eb87329e1871993aa5935a0b9ed83c96b322efa21898a160a95e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415669"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Numaralama öğesini ilk öğeye sıfırlar.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra Next yöntemine yapılan [sonraki](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) çağrı, numaralamanın ilk öğesini döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
