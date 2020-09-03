---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721827"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Program düğümüne, ilişkili programa iliştirme girişimi hakkında bildirim gönderilmesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, bir iliştirme işleminin bildirimini almak ve iliştirme işlemini iptal etmek için bir fırsat sağlamak üzere [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimini uygulayan aynı sınıfa uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 `QueryInterface`Yöntemi bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesinde çağırarak bu arabirimi elde edin. Program düğümüne iliştirme işlemini durdurma şansı vermek için [iliştirme](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminden önce [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi çağrılmalıdır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|İlişkili programa ekler veya Attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, kullanım dışı [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) yöntemi için tercih edilen alternatiftir. Tüm hata ayıklama motorları işleviyle her zaman yüklenir `CoCreateInstance` , diğer bir deyişle, hata ayıklanan programın adres alanının dışında oluşturulur.

 Yöntemi önceki bir uygulama, `IDebugProgramNode2::Attach_V7` `GUID` hata ayıklamakta olan programın yalnızca ayarlamadıysa, yalnızca [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yönteminin uygulanması gerekir.

 Yöntemin önceki bir uygulamasında `IDebugProgramNode2::Attach_V7` sağlanmış geri çağırma arabirimi kullanılıyorsa, bu Işlevin [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminin bir uygulamasına taşınması gerekir ve `IDebugProgramNodeAttach2` arabirimin uygulanması gerekmez.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
