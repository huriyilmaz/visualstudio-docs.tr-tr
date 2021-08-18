---
description: Geçerli belge konumunun aralığını alın.
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a262287e6dc84316686f1132ed0ac496eee35e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111260"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Geçerli belge konumunun aralığını alın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametreler
`pdwBegOffset`\
[in, out] Aralığın başlangıç konumu için uzaklık. Bu bilgi gerekli yoksa bu parametreyi null değere ayarlayın.

`pdwEndOffset`\
[in, out] Aralığın bitiş konumu için uzaklık. Bu bilgi gerekli yoksa bu parametreyi null değere ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Konum kesme noktası için belge konumunda belirtilen aralık, hata ayıklama altyapısı (DE) tarafından koda katkıda bulunan bir deyimi önceden aramak için kullanılır. Örneğin, aşağıdaki kodu düşünün:

```
Line 5: // comment
Line 6: x = 1;
```

 5. satır, hata ayıklaması yapılan programa kod katmaz. 5. satırda kesme noktası ayarlayıcı, DE'nin koda katkıda bulunan ilk satır için belirli bir miktarı aramasını istiyorsa, hata ayıklayıcı bir kesme noktası doğru yerleştirilse ek aday satırları içeren bir aralık belirtir. Ardından DE, kesme noktası kabul eden bir satır bulana kadar bu satırlarda ileri doğru arama yaptı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
