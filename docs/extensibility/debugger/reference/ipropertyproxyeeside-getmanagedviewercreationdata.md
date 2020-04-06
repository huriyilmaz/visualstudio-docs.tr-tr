---
title: ipropertyproxyeeside::getmanagedviewercreationData | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714959"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Bu görüntüleyiciyi anında anlabilmek için bu özellik türü için görüntüleyici hakkındaki bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
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
[çıkış] Bu nesneyi tutan derlemenin adını döndürür.

`assemBytes`\
[çıkış] Bu nesnenin montaj baytlarını içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi döndürür (bayt yoksa bu geçersiz bir değerdir).

`assemPdb`\
[çıkış] Bu `IEEDataStorage` nesne için sembol deposu bilgilerini içeren bir nesne döndürür (bu, sembol deposu yoksa bu geçersiz bir değerdir).

`className`\
[çıkış] Bu nesneyi içeren sınıf adını döndürür.

`alr`\
[çıkış] Assemblyin yerini gösteren [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) numaralandırmasından bir değer verir.

`replacementOk`\
[çıkış] Bu nesnenin`TRUE`değeri değiştirilebiliyorsa sıfırsız ( ) döndürür; sıfır`FALSE`( ) nesne salt okunursa.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yönetilen bir görüntüleyicianlık için tür görüntüleyiciler tarafından kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
