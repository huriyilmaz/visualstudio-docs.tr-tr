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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7800956063236055962eb295a3101b40f99f22a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072207"
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
