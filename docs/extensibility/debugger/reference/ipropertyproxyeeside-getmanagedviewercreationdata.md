---
description: Bu görüntüleyicinin örneğini oluşturmak için bu özellik türü için Görüntüleyici hakkındaki bilgileri alır.
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e264d80bc940d4091f380d401ba24719a46e36fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042861"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Bu görüntüleyicinin örneğini oluşturmak için bu özellik türü için Görüntüleyici hakkındaki bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parametreler
`assemName`\
dışı Bu nesneyi tutan derlemenin adını döndürür.

`assemBytes`\
dışı Bu nesnenin derleme baytlarını içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi döndürür (kullanılabilir bayt yoksa bu null değerdir).

`assemPdb`\
dışı `IEEDataStorage` Bu nesnenin sembol deposu bilgilerini içeren bir nesne döndürür (kullanılabilir sembol deposu yoksa bu null bir değerdir).

`className`\
dışı Bu nesneyi içeren sınıf adını döndürür.

`alr`\
dışı [Assemblylocresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) numaralandırmasından derlemenin konumunu gösteren bir değer döndürür.

`replacementOk`\
dışı `TRUE`Bu nesnenin değeri değiştirilebiliyorsa sıfır olmayan () değerini döndürür; `FALSE` nesne salt okunurdur sıfır ().

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yönetilen bir Görüntüleyici örneği oluşturmak için tür Görselleştiriciler tarafından kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
