---
title: Idebugportpicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724841"
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
