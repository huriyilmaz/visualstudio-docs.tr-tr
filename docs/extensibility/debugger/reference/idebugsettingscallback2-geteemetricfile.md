---
description: Ad veya ölçüm verilen ifade değerlendirici ölçüm dosyasını alır.
title: 'IDebugSettingsCallback2:: GetEEMetricFile | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ba7f6008e6b513a99c1d8e9c21d78e99938c926
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165793"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Ad veya ölçüm verilen ifade değerlendirici ölçüm dosyasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEEMetricFile(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricFile(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parametreler
`guidLang`\
'ndaki Programlama dilinin benzersiz tanıtıcısı.

`guidVendor`\
'ndaki Satıcının benzersiz tanıtıcısı.

`pszMetric`\
'ndaki Ölçümün adı.

`pbstrValue`\
dışı Ölçüm dosyasının içeriğini bir dize olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
