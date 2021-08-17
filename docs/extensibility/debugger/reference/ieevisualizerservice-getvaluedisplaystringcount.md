---
description: Belirtilen özellik veya alan için görüntülenmek üzere değer dizelerinin sayısını verir.
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaabad975a57e18c9257df178b29b594d892441482db30fcd00836c322fb0169
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389429"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Belirtilen özellik veya alan için görüntülenmek üzere değer dizelerinin sayısını verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parametreler
`displayKind`\
[in] [DisplayKind numaralama](../../../extensibility/debugger/reference/displaykind.md) değeri.

`propertyOrField`\
[in] Bir özelliği veya alanı temsil eden [bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimi.

`pcelt`\
[out] Görüntülemek için değer dizelerinin sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
