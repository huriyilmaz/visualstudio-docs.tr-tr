---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732569"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Özel özniteliğin adı verilen özel öznitelik baytlarını edinir.

## <a name="syntax"></a>Söz dizimi

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
