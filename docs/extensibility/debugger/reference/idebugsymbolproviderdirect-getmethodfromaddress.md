---
description: Belirtilen hata ayıklama adresine yöntemiyle ilgili bilgileri alın.
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26a225180d86b44903564d099b219008703bccb3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095861"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Belirtilen hata ayıklama adresine yöntemiyle ilgili bilgileri alın.

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
[in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi tarafından temsil edilen hata ayıklama adresi.

`pGuid`\
[out] Modülün benzersiz tanımlayıcısı.

`pAppID`\
[out] Uygulama etki alanının tanımlayıcısı.

`pTokenClass`\
[out] İçeren sınıfı temsil eden belirteç.

`pTokenMethod`\
[out] Modülü temsil eden belirteç.

`pdwOffset`\
[out] Parametrenin başındaki bayt cinsinden `pAddress` uzaklık.

`pdwVersion`\
[out] Yöntemin sürüm numarası.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
