---
title: IDebugDocumentPosition2::GetRange | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731669"
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
[içinde, dışarı] Başlangıç pozisyonuyla doldurulmuş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı. Bu bilgiler gerekli değilse, bu bağımsız değişkeni null değere ayarlayın.

`pEndPosition`\
[içinde, dışarı] Bitiş pozisyonuyla doldurulmuş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı. Bu bilgiler gerekli değilse, bu bağımsız değişkeni null değere ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir konum kesme noktası için belge konumunda belirtilen aralık, hata ayıklama altyapısı (DE) tarafından koda gerçekten katkıda bulunan bir ifadeyi önceden aramak için kullanılır. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```
Line 5: // comment
Line 6: x = 1;
```

 Satır 5, debugged olan programa hiçbir kod katkıda bulunmaz. Satır 5'teki kesme noktasını ayarlayan hata ayıklayıcı, DE'nin koda katkıda bulunan ilk satır için belirli bir miktarı ileri aramasını istiyorsa, hata ayıklayıcı kesme noktasının düzgün yerleştirilebileceği ek aday satırları içeren bir aralık belirtir. DE daha sonra bir kesme noktası kabul edebilecek bir satır bulana kadar bu satırları ileriye doğru arama olacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
