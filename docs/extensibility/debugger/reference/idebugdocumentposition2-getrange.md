---
description: Bu belge konumu için aralığı alır.
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 211003c3d54b7f37979240e400e373db2782ac2a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634985"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Bu belge konumu için aralığı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametreler
`pBegPosition`\
[in, out] Başlangıç [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) doldurulan bir yapıdır. Bu bilgi gerekli yoksa bu bağımsız değişkeni null değere ayarlayın.

`pEndPosition`\
[in, out] Bitiş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) doldurulan bir yapıdır. Bu bilgi gerekli yoksa bu bağımsız değişkeni null değere ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Konum kesme noktası için belge konumunda belirtilen aralık, hata ayıklama altyapısı (DE) tarafından koda katkıda bulunan bir deyimi önceden aramak için kullanılır. Örneğin, aşağıdaki kodu düşünün:

```
Line 5: // comment
Line 6: x = 1;
```

 5. satır, hata ayıklaması yapılan programa kod katmaz. 5. satırda kesme noktası ayarlayıcı, DE'nin koda katkıda bulunan ilk satır için belirli bir miktarda arama yapmak istiyorsa, hata ayıklayıcı bir kesme noktası düzgün yerleştirilse ek aday satırları içeren bir aralık belirtir. Ardından DE, kesme noktası kabul eden bir satır bulana kadar bu satırlarda ileri doğru arama yaptı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
