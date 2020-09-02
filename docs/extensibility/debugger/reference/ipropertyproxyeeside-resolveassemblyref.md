---
title: 'IPropertyProxyEESide:: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c54945b0c89fb9608fab6aa70dcc63a7c6ae42df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714883"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Belirtilen yönetilen derleme başvurusunun konumunu belirler.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parametreler
`assemName`\
'ndaki Çözülecek derlemenin adı.

`assemBytes`\
dışı Başvuruyla ilişkili derleme baytlarını içeren bir [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nesnesi döndürür.

`assemPdb`\
dışı `IEEDataStorage` Bu başvuruyla ilişkili sembol deposu verilerini içeren bir nesne döndürür.

`assemLocation`\
dışı Bu başvurunun yol konumunu döndürür.

`alr`\
dışı Bu başvurunun derlemenin konumunu gösteren [Assemblylocresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) numaralandırmasından bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, genellikle özel ifade değerlendiricisi tarafından uygulanmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
