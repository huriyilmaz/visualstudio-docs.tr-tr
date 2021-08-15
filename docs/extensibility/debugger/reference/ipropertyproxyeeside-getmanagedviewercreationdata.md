---
description: Bu görüntüleyicinin örneğini almak için bu özellik türü için görüntüleyiciyle ilgili bilgileri alın.
title: IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
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
ms.openlocfilehash: 3044abff780c0b7798c7c311cf32199166230c0315a12dfc6caf47ca23cc9da4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321395"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Bu görüntüleyicinin örneğini almak için bu özellik türü için görüntüleyiciyle ilgili bilgileri alın.

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
[out] Bu nesneyi tutan derlemenin adını döndürür.

`assemBytes`\
[out] Bu nesnenin derleme baytlarını içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi döndürür (kullanılabilir bayt yoksa bu null değerdir).

`assemPdb`\
[out] Bu nesne için sembol deposu bilgilerini içeren bir nesne döndürür (herhangi bir sembol deposu yoksa bu null `IEEDataStorage` değerdir).

`className`\
[out] Bu nesneyi içeren sınıf adını döndürür.

`alr`\
[out] [ASSEMBLYLOCRESOLUTION enumerasyonundan](../../../extensibility/debugger/reference/assemblylocresolution.md) derlemenin konumunu belirten bir değer döndürür.

`replacementOk`\
[out] Bu nesnenin değeri değiştirilebilecekse sıfır olmayan ( ) döndürür; nesne salt `TRUE` okunursa sıfır ( `FALSE` ) .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, tür görselleştiricileri tarafından yönetilen görüntüleyici örneği için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
