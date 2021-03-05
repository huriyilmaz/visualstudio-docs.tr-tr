---
description: Bir ölçümün adı verilen benzersiz tanımlayıcısını alır.
title: 'IDebugSettingsCallback2:: GetMetricGuid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricGuid
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 504a47de04fde7aa0c630bf17e0a1c4ac24723ce
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168679"
---
# <a name="idebugsettingscallback2getmetricguid"></a>IDebugSettingsCallback2::GetMetricGuid
Bir ölçümün adı verilen benzersiz tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMetricGuid(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
private int GetMetricGuid(
   string   pszType,
   ref Guid guidSection,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>Parametreler
`pszType`\
'ndaki Ölçüm türü.

`guidSection`\
'ndaki Bölümün benzersiz tanıtıcısı.

`pszMetric`\
'ndaki Ölçümün adı.

`pguidValue`\
dışı Ölçümün benzersiz tanımlayıcısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
