---
title: IDebugProgramNodeAttach2 | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721827"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Bir program düğümünün ilişkili programa ekleme girişimi hakkında bilgilendirilmesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, bir ekleme işlemi bildirimini almak ve ekleme işlemini iptal etme fırsatı sağlamak için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimini uygulayan aynı sınıfta uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Yöntemi bir `QueryInterface` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesinde arayarak bu arabirimi edinin. Program düğümüne ekleme işlemini durdurma şansı vermek için [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminden önce çağrılmalıdır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|İlişkili programa bağlanır veya ekleme işlemini [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.|

## <a name="remarks"></a>Açıklamalar
 Bu arayüz, [amortismana](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Attach_V7 yöntemine tercih edilen alternatiftir. Tüm hata ayıklama motorları `CoCreateInstance` her zaman işlevi ile yüklenir, yani, onlar debugged olan programın adres alanı dışında anında.

 `IDebugProgramNode2::Attach_V7` Yöntemin önceki bir uygulaması yalnızca `GUID` debugged olan programın ayarlanması ise, yalnızca [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi uygulanması gerekir.

 Yöntemin `IDebugProgramNode2::Attach_V7` önceki bir uygulaması sağlanan geri arama arabirimi kullanılırsa, bu işlevselliğin [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminin `IDebugProgramNodeAttach2` bir uygulamasına taşınması gerekir ve arabirimin uygulanması gerekmez.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
