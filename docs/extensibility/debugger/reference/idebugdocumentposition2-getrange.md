---
description: Bu belge konumunun aralığını alır.
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119483"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Bu belge konumunun aralığını alır.

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
[in, out] Başlangıç konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.

`pEndPosition`\
[in, out] Bitiş konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir konum kesme noktası için bir belge konumunda belirtilen Aralık, aslında koda katkıda bulunan bir ifadenin önünde aramak için hata ayıklama altyapısı (DE) tarafından kullanılır. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```
Line 5: // comment
Line 6: x = 1;
```

 5. satır hata ayıklamakta olan programa kod vermez. 5. satırda kesme noktasını ayarlayan hata ayıklayıcı, kod katkıda bulunan ilk satır için belirli bir miktarı ileri doğru aramak isterse, hata ayıklayıcı, bir kesme noktasının düzgün şekilde yerleştirilebileceği ek aday çizgileri içeren bir Aralık belirler. Ayrıca, bir kesme noktası kabul edebilecek bir çizgi bulunana kadar bu satırlarda ileriye doğru arama yapılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
