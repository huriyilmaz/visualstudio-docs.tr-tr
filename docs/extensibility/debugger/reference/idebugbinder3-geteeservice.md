---
description: Bu yöntem istenen hizmeti döndürür.
title: 'IDebugBinder3:: GetEEService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ecd439ba1af40a54512c3ef15efb4728c8c54a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167678"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Bu yöntem istenen hizmeti döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parametreler
`vendor`\
[in] `GUID` bir satıcı (null değer kabul edilebilir).

`language`\
[in] `GUID` bir dil (null değer kabul edilebilir).

`iid`\
[in] `IID` hizmeti edinin.

`ppService`\
dışı İstenen hizmete yönelik bir arabirim.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `IID`Tür görselleştiricisi hizmeti 'nin kullanılabilir olup olmadığını görmek Için [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) arabirimine ( `IID_IEEVisualizerServiceProvider` ) geçin. Bu durumda, ifade değerlendirici, tür görselleştiricileri desteklemek için [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) arabirimini alabilir. Ayrıntılar için bkz. [verileri görselleştirme ve görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Verileri Görselleştirme ve Görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md)
