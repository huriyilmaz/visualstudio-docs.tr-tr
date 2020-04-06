---
title: IDebugProperty2::SetValueAsString | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721244"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Belirli bir dizeden bir özelliğin değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametreler
`pszValue`\
[içinde] Ayarlanacak değeri içeren bir dize.

`nRadix`\
[içinde] Herhangi bir sayısal bilgi nin yorumlanmasında kullanılacak bir radix. Bu, radix'i otomatik olarak belirlemeye çalışmak için 0 olabilir.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden en büyük süreyi belirtir. Süresiz beklemek için kullanın. `INFINITE`

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür. Aşağıdaki tablo diğer olası değerleri gösterir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Dize bir özellik değerine dönüştürülemedi veya özellik değeri ayarlanamadı.|
|`E_SETVALUE_VALUE_IS_READONLY`|Tesis salt okunur.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
