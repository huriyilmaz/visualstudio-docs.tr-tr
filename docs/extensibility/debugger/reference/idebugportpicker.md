---
title: IDebugPortPicker | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724841"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Bağlantı noktasını seçmek için özelleştirilmiş bir ara birimi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim liman tedarikçileri tarafından uygulanır. Bir bağlantı noktası tedarikçisi, bağlantı noktası seçicisini CLSID olarak `metricPortPickerCLSID` teşhir ederek ve ölçümü açığa çıkan CLSID'ye işaret ederek tanımlar.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugPortPicker`.

|Yöntem|Açıklama|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Kullanıcının bir bağlantı noktası seçmesine izin veren belirtilen iletişim kutusunu görüntüler.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Servis sağlayıcıyı ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
