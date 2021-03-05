---
description: Belirli bir dizeden bir özelliğin değerini ayarlar.
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b86de71cd6df3e028697518de8c6faccad7e2336
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166729"
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
'ndaki Ayarlanacak değeri içeren bir dize.

`nRadix`\
'ndaki Herhangi bir sayısal bilgiyi yorumlamak için kullanılan bir taban. Bu, taban x 'i otomatik olarak belirlemeyi denemek için 0 olabilir.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Dize bir özellik değerine dönüştürülemedi veya özellik değeri ayarlanamadı.|
|`E_SETVALUE_VALUE_IS_READONLY`|Özellik salt okunurdur.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
