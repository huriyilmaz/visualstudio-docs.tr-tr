---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731631"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Geçerli belge konumunun aralığını alır.

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
[içinde, dışarı] Aralığın başlangıç konumu için ofset. Bu bilgiler gerekli değilse, bu parametreyi null değerine ayarlayın.

`pdwEndOffset`\
[içinde, dışarı] Aralığın bitiş konumu için ofset. Bu bilgiler gerekli değilse, bu parametreyi null değerine ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir konum kesme noktası için belge konumunda belirtilen aralık, hata ayıklama altyapısı (DE) tarafından koda gerçekten katkıda bulunan bir ifadeyi önceden aramak için kullanılır. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```
Line 5: // comment
Line 6: x = 1;
```

 Satır 5, debugged olan programa hiçbir kod katkıda bulunmaz. Satır 5'teki kesme noktasını ayarlayan hata ayıklayıcı, DE'nin koda katkıda bulunan ilk satır için belirli bir miktarı ileri aramasını istiyorsa, hata ayıklayıcı kesme noktasının doğru yerleştirilebileceği ek aday satırları içeren bir aralık belirtir. DE daha sonra bir kesme noktası kabul edebilecek bir satır bulana kadar bu satırları ileriye doğru arama olacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
