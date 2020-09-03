---
title: 'IDebugPortSupplierLocale2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f35e4f2732427045fac982454ce9f7290a6dc970
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724311"
---
# <a name="idebugportsupplierlocale2setlocale"></a>IDebugPortSupplierLocale2::SetLocale
Bağlantı noktası sağlayıcısı için yerel ayarı ayarlar.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametreler
`wLangID`\
Ayarlanacak yerel ayar için tanımlayıcı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)
