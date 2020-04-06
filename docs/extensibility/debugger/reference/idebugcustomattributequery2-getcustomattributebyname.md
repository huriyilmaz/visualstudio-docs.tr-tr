---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732569"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Özel öznitelik adı verilen özel öznitelikleri alır.

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
[içinde] Aramak için özel öznitelik adını içeren bir dize.

`ppBlob`\
[içinde, dışarı] Özel öznitelik baytları ile doldurulan bir dizi.

`pdwLen`\
[içinde, dışarı] `ppBlob` Dizide döndürülecek maksimum bayt sayısını belirtir ve diziye gerçekten yazılmış bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, özel öznitelik yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanılabilir `ppBlob` öznitelik bayt sayısını döndürmek için parametreyi null değerine ayarlayın. Ardından bir dizi ayırın ve bu `ppBlob` diziyi parametre için geçirin.

 Öznitelik baytlar, özel özniteliğin ham verilerini temsil eder.

 `ppBlob` Ve `pdwLen` parametreler null değerine ayarlanmışsa, bu yöntem özel özniteliğin yalnızca var olup olmadığını belirlemek için kullanılabilir. Daha kolay bir alternatif, ancak, [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) yöntemi aramaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
