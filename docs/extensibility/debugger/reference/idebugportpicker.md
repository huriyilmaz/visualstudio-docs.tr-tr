---
description: Bağlantı noktasını seçmek için özelleştirilmiş bir kullanıcı arabirimini temsil eder.
title: Idebugportpicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8390c8a055a9c919bb1a35d8f3288fc810e5329d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072260"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Bağlantı noktasını seçmek için özelleştirilmiş bir kullanıcı arabirimini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, bağlantı noktası tedarikçileri tarafından uygulanır. Bir bağlantı noktası tedarikçisinin bağlantı noktası seçiciyi bir CLSID olarak işaretleyerek ve `metricPortPickerCLSID` ortaya ÇıKAN CLSID üzerinde ölçerek tanımlar.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPortPicker` .

|Yöntem|Açıklama|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Kullanıcının bir bağlantı noktası seçmesini sağlayan, belirtilen iletişim kutusunu görüntüler.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Hizmet sağlayıcıyı ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
