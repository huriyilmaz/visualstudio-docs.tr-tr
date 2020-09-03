---
title: 'Idebugsymbolproviderdirect:: Getmethodfromadkıya| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a062056f4a61521966417e9923a17f6d85b991a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718950"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Belirtilen hata ayıklama adresinde yöntemi hakkındaki bilgileri alır.

## <a name="syntax"></a>Söz dizimi

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
