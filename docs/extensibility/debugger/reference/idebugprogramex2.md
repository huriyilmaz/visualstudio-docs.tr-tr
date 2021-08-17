---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) bir programa iliştirmelerini ve bir programla ilişkili program düğümünü almasını sağlar.
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 315fa87aa40a0642a3f383034664a5812679e6df
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126407"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) bir programa iliştirmelerini ve bir programla ilişkili program düğümünü almasını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi, SDM 'nin programa bağlı tüm oturumları izlemesine izin vermek için, aynı zamanda, SDM 'yi bir programa ekleyebilmesine izin vermek üzere [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimiyle aynı nesne üzerinde uygular. Özel bağlantı noktası sağlayıcısı, seçerse bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 SDM, [](/cpp/atl/queryinterface) `IDebugProgram2` programlara eklenmiş olan oturumları izlemek için bu arabirimi almak üzere bir arabirimdeki QueryInterface 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProgramEx2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[İliştir](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Bir oturuma program iliştirir.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Bir programla ilişkili program düğümünü alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, SDM ve program arasında özeldir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
