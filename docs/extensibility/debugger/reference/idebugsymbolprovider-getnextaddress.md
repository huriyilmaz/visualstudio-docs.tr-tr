---
title: 'IDebugSymbolProvider:: GetNextAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b314ab7006d6bbe65136451aeee6c5200cf7980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719200"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Bir yöntemde belirli bir hata ayıklama adresini izleyen hata ayıklama adresini alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parametreler
`pAddress`\
'ndaki Verilen hata ayıklama adresi.

`fStatementOnly`\
'ndaki TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlandırır.

`ppAddress`\
dışı Sonraki hata ayıklama adresini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Geçerli bir `HRESULT` , genellikle S_OK döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
