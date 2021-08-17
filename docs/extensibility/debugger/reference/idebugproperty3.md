---
title: IDebugProperty3 | Microsoft Docs
description: Bu arabirim, özelliğiyle ilişkili rastgele olarak uzun bir dize alma, özelliğiyle benzersiz bir kimliği ilişkilendirilerek, özelliği için özel görüntüleyicilerin listesini alma ve bir özelliğin değerini sonuçta ortaya çıkan hataları bildirme özelliğiyle ayarlama desteği sağlar.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9f4e601258e14783c808652c6dd249e9709be554
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087710"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Bu arabirim aşağıdakiler için destek sağlar:

- özelliğiyle ilişkili rastgele uzun bir dizeyi alma.

- Benzersiz bir kimliği özelliğiyle irdeler.

- Özelliği için özel görüntüleyicilerin listesini alma.

- Bir özelliğin değerini, sonuçta ortaya çıkan hataları bildirebilme özelliğiyle ayarlama

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), uzun dizeler, özellik kimlikleri ve özel görüntüleyiciler için destek sağlamak üzere [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan aynı nesnede bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için bir arabirimde [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty2` çağrısı yapmak.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 'den devralınan yöntemlere ek `IDebugProperty2` `IDebugProperty3` olarak, arabirimi aşağıdaki yöntemleri gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|özelliğiyle ilişkili dizenin uzunluğunu döndürür.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Kullanıcı tarafından sağlanan arabellekte dizeyi döndürür.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Bu özellik için benzersiz bir kimlik oluşturur.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Bu özellik için benzersiz kimliği yok eder.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Bu özelliğin görüntülen diğer özel görüntüleyici sayısını döndürür.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Bu özelliğin görüntülenebilirsiniz özel görüntüleyiciler listesini döndürür.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Bir sorun olursa hata iletisi döndürerek bu özelliğin değerini ayarlar.|

## <a name="remarks"></a>Açıklamalar
- [SetValueAsStringWithError,](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) bir özelliğin değerini ayarlamak için oturum hata ayıklama yöneticisi (SDM) için tercih edilen yöntemdir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
