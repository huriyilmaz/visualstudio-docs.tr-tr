---
description: Bir program düğümüne, ilişkili programa ekleme girişiminin bildir bildir 1000000000000000000000000000000000000000000
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a579d985cea401f855934b1966e387c7a5a1832a12f2f347b734f6a7e035f7f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449189"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Bir program düğümüne, ilişkili programa ekleme girişiminin bildir bildir 1000000000000000000000000000000000000000000

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, bir ekleme işleminin bildirimini almak ve ekleme işlemini iptal etme fırsatı sağlamak için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimini uygulayan aynı sınıfta uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 `QueryInterface` [Bir IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesinde yöntemini çağırarak bu arabirimi alın. Program düğümüne ekleme işlemini durdurma şansı vermek [için Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi öncesinde [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yönteminin çağrılsı gerekir.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Bu arabirim aşağıdaki yöntemi kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|İlişkili programa iliştirer veya attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine karşılar.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, kullanım dışı Attach_V7 [tercih](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) edilir. Tüm hata ayıklama altyapıları her zaman işleviyle birlikte yüklenir; diğer bir ifadeyle, bunlar hata ayıklaması yapılan `CoCreateInstance` programın adres alanı dışında örnekleniyor.

 Yöntemin önceki bir uygulaması yalnızca hata ayık olan programın ayarını yapmaksa `IDebugProgramNode2::Attach_V7` `GUID` yalnızca [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yönteminin uygulanması gerekir.

 Yöntemin önceki bir uygulaması sağlanan geri çağırma arabirimini kullandı ise, bu işlevin Attach yönteminin uygulamasına geçirilmesi gerekir ve arabirimin `IDebugProgramNode2::Attach_V7` [](../../../extensibility/debugger/reference/idebugengine2-attach.md) `IDebugProgramNodeAttach2` uygulanmasına gerek olmaz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
