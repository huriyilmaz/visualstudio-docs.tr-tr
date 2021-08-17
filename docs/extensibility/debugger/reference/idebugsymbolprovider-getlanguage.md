---
description: Bu yöntem, kodu hata ayıklama adreslerinde derlemek için kullanılan dili alır.
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0f5f71ddc3989a6aa3c3904d8f759c9d83a4bb7eb42587a39f7b23841fb1d4a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448799"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Bu yöntem, kodu hata ayıklama adreslerinde derlemek için kullanılan dili alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
[in] [IDebugAddress arabirimiyle temsil edilen bir adres](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi.

`pguidLanguage`\
[out] Dili `GUID` belirten bir döndürür.

`pguidLanguageVendor`\
[out] Dil `GUID` satıcısını belirten bir döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı, doğru ifade değerlendiriciyi seçmek için gereken bilgileri almak için bu yöntemi arar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
