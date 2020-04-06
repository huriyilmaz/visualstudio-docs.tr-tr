---
title: IDebugProgramNode2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721918"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Bu arabirim, debugged olabilir bir programı temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) veya özel bir bağlantı noktası tedarikçisi, hata ayıklanabilen bir programı temsil etmek için bu arabirimi uygular. Bu arabirim genellikle [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimini uygulayan aynı nesne üzerinde uygulanır. Bu arabirim [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)çağırarak kaydedilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi döndürmek için [GetProviderProgramNode'u](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) arayın. Özel bir bağlantı noktası tedarikçisi [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)bir çağrı yoluyla bu arayüzü alır. Bir DE bu arabirimi [Ekle'ye](../../../extensibility/debugger/reference/idebugengine2-attach.md)bir çağrı aracılığıyla alır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgramNode2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Bir programın adını alır.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Bir program barındırma işleminin adını alır.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Bir programı barındıran işlem için sistem işlem tanımlayıcısını alır.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Kaldırıl -mış. KULLANMAYıN.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Kaldırıl -mış. KULLANMAYıN. Alternatif bir yaklaşım için [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimine bakın.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Bu programı çalıştıran DE'nin adını ve tanımlayıcısını alır.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Kaldırıl -mış. KULLANMAYıN.|

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi (SDM) genellikle bu arabirimi elde etmek için [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) çağırır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
