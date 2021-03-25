---
description: Özel özniteliğin adı verilen özel öznitelik baytlarını edinir.
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd8b1793bad585dd808ebd812b610cd68aabc129
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077609"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Özel özniteliğin adı verilen özel öznitelik baytlarını edinir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parametreler
`pszCustomAttributeName`\
'ndaki Aranacak özel özniteliğin adını içeren bir dize.

`ppBlob`\
[in, out] Özel öznitelik baytları ile doldurulmuş bir dizi.

`pdwLen`\
[in, out] Dizide döndürülecek en fazla bayt sayısını belirtir `ppBlob` ve gerçekten diziye yazılan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, özel öznitelik yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `ppBlob`Kullanılabilir öznitelik baytları sayısını döndürmek için parametreyi null değere ayarlayın. Sonra bir dizi ayırın ve bu diziyi parametresi için geçirin `ppBlob` .

 Öznitelik baytları özel özniteliğin ham verilerini temsil eder.

 `ppBlob`Ve `pdwLen` parametreleri null bir değere ayarlanırsa, bu yöntem özel özniteliğin yalnızca mevcut olup olmadığını anlamak için kullanılabilir. Ancak, daha kolay bir alternatif, [ıcustomattributedefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) yöntemini çağırmaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
