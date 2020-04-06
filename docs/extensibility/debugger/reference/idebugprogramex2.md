---
title: IDebugProgramEx2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722335"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) bir programa bağlanmasını ve programla ilişkili program düğümlerini almalarına olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, SDM'nin bir programa bağlanmasına izin vermek ve aynı zamanda bağlantı noktası tedarikçisinin programa bağlı tüm oturumları izlemesine izin vermek için bu arabirimi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimiyle aynı nesne üzerinde uygular. Özel bağlantı noktası tedarikçisi isterse bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM, programlara iliştirilen oturumları izlemek için bu arabirimi elde etmek için queryInterface'i bir `IDebugProgram2` arabirimüzerinde çağırır. [QueryInterface](/cpp/atl/queryinterface)

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProgramEx2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[İliştir](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Bir oturuma program bağlar.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Program düğümlerini bir programla ilişkilendirir.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim SDM ve program arasında özeldir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portpriv.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
