---
description: Özel özniteliğin adına göre özel öznitelik baytlarını elde eder.
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20f4cba0d826a7a9b608f1fc56fde1a35ae54c0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627447"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Özel özniteliğin adına göre özel öznitelik baytlarını elde eder.

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
[in] Arama için özel özniteliğin adını içeren bir dize.

`ppBlob`\
[in, out] Özel öznitelik baytları ile doldurulmuş bir dizi.

`pdwLen`\
[in, out] Dizide döndüren en fazla bayt sayısını `ppBlob` belirtir ve aslında diziye yazılan bayt sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK veya S_FALSE özniteliği yoksa bu değeri döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanılabilir `ppBlob` öznitelik baytlarının sayısını döndüren parametreyi null değere ayarlayın. Ardından bir dizi ayırarak parametresi için bu diziyi `ppBlob` iletir.

 Öznitelik baytları, özel özniteliğin ham verilerini temsil eder.

 ve `ppBlob` parametreleri `pdwLen` null değere ayarlanırsa, özel özniteliğin yalnızca mevcut olup olmadığını belirlemek için bu yöntem kullanılabilir. Ancak daha kolay bir alternatif de [IsCustomAttributeDefined yönteminin çağrılmaktır.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
