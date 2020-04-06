---
title: IDebugÖzellik3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721045"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Bu arabirim için destek sağlar:

- Özellik ile ilişkili rasgele uzun bir dize alma.

- Tesisle benzersiz bir kimlik ilişkilendirme.

- Özellik için özel görüntüleyenlerin listesini alma.

- Ortaya çıkan hataları bildirme özelliğiyle bir özelliğin değerini ayarlama

## <a name="syntax"></a>Sözdizimi

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), uzun dizeleri, özellik disleri ve özel görüntüleyenler için destek sağlamak için [IDebugProperty2'yi](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan aynı nesneye bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi `IDebugProperty2` elde etmek için [queryinterface'i](/cpp/atl/queryinterface) bir arabirimden arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Devralınan yöntemlere ek `IDebugProperty2`olarak, `IDebugProperty3` arabirim aşağıdaki yöntemleri ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Özellik ile ilişkili dize uzunluğunu döndürür.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Kullanıcı tarafından sağlanan arabellekteki dizeyi döndürür.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Bu özellik için benzersiz bir kimlik oluşturur.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Bu özellik için benzersiz kimliği yok eder.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Bu özelliğin görüntülenebileceği özel görüntüleyenlerin sayısını döndürür.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Bu özelliğin görüntülenebileceği özel görüntüleyenlerin listesini verir.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Bir şey yanlış gittiyse bir hata iletisi döndürerek bu özelliğin değerini ayarlar.|

## <a name="remarks"></a>Açıklamalar
- [SetValueAsStringWithError,](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) oturum hata ayıklama yöneticisinin (SDM) bir özelliğin değerini ayarlamasının tercih edilen yoludur.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
