---
description: Belirtilen hata ayıklama adresinde yöntemi hakkındaki bilgileri alır.
title: 'Idebugsymbolproviderdirect:: Getmethodfromadkıya| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dea6367280217f42238a56a56a6ce0e0e6f92b47
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149502"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Belirtilen hata ayıklama adresinde yöntemi hakkındaki bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
'ndaki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi tarafından temsil edilen hata ayıklama adresi.

`pGuid`\
dışı Modülün benzersiz tanıtıcısı.

`pAppID`\
dışı Uygulama etki alanının tanımlayıcısı.

`pTokenClass`\
dışı Kapsayan sınıfı temsil eden belirteç.

`pTokenMethod`\
dışı Modülünü temsil eden belirteç.

`pdwOffset`\
dışı Parametrenin başından itibaren bayt cinsinden bir konum `pAddress` .

`pdwVersion`\
dışı Metodun sürüm numarası.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
