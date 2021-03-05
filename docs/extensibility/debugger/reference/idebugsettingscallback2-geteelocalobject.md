---
description: Ölçüm adı verilen bir ifade değerlendirici yerel nesnesi alır.
title: 'IDebugSettingsCallback2:: GetEELocalObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72ff072cdb6c0431a7b04e644f71186c91763efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168770"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
Ölçüm adı verilen bir ifade değerlendirici yerel nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

## <a name="parameters"></a>Parametreler
`guidLang`\
'ndaki Programlama dilinin benzersiz tanıtıcısı.

`guidVendor`\
'ndaki Satıcının benzersiz tanıtıcısı.

`pszMetric`\
'ndaki Ölçümün adı.

`ppUnk`\
dışı İfade değerlendirici yerel nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
