---
title: 'IDebugField:: eşittir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c19e8860fb9ed9cbd65efe7fa72fd920a01622ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915481"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Bu yöntem, bu alanı eşitlik için belirtilen alanla karşılaştırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parametreler
`pField`\
'ndaki Bu ile Karşılaştırılacak alan.

## <a name="return-value"></a>Dönüş Değeri
 Alanlar aynıysa, döndürür `S_OK` . Alanlar farklıysa, `S_FALSE.` Aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
