---
description: Bir yöntemde belirli bir hata ayıklama adresini izleyen hata ayıklama adresini alır.
title: 'IDebugSymbolProvider:: GetNextAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35016b6b332e1ed4fe81ca784242f1081cb885d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029638"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Bir yöntemde belirli bir hata ayıklama adresini izleyen hata ayıklama adresini alır.

## <a name="syntax"></a>Sözdizimi

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
