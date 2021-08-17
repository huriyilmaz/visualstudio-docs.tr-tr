---
description: Belirli bir dizeden bir özelliğin değerini ayarlar.
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d71f6926e9b973f83ae8f6d8e4a64ac127eaca6cf85e335cb6970c261c56840
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449020"
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
[in] Ayarlandır değerini içeren bir dize.

`nRadix`\
[in] Herhangi bir sayısal bilgiyi yorumlamak için kullanılacak radyal. Radyanı otomatik olarak belirlemeye çalışırken bu 0 olabilir.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek için milisaniye cinsinden en uzun süreyi belirtir. Süresiz `INFINITE` olarak beklemek için kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür. Aşağıdaki tabloda diğer olası değerler yer alır.

|Değer|Açıklama|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Dize bir özellik değerine dönüştürüledi veya özellik değeri ayarlandı.|
|`E_SETVALUE_VALUE_IS_READONLY`|özelliği salt okunur özelliktir.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
