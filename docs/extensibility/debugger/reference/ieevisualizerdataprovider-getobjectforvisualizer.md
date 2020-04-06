---
title: IEEVisualizerDataProvider::GetObjectForVisualizer | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2aa1e20dd8639ce089ebe851116a15bf61e35ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718123"
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
Bu yöntem, bu görselleştiricinin temsil ettiği nesneyi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`ppObject`\
[çıkış] Bu görselleştirici tarafından temsil edilen nesne

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 `GetObjectForVisualizer`nesnenin önbelleğe alınmış bir sürümünü döndürmesine izin verilir. Arayan nesnenin güncel olduğundan emin olmak istiyorsa, [getNewObjectForVisualizer'ı](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)arayacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
