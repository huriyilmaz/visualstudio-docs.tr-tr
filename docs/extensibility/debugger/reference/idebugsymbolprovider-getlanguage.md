---
description: Bu yöntem, hata ayıklama adresinde kodu derlemek için kullanılan dili alır.
title: 'IDebugSymbolProvider:: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86387e86261a91b77793e9a31ae4b415983e2c5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168562"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Bu yöntem, hata ayıklama adresinde kodu derlemek için kullanılan dili alır.

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
'ndaki Bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi tarafından temsil edilen bir adres nesnesi.

`pguidLanguage`\
dışı `GUID` Dili belirten bir döndürür.

`pguidLanguageVendor`\
dışı `GUID` Dili satıcıyı belirten bir döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı, doğru ifade değerlendiricisi seçmek için gereken bilgileri almak üzere bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
