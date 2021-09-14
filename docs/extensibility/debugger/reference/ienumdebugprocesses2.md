---
description: Bu arabirim, hata ayıklama bağlantı noktası üzerinde çalışan işlemi numaralandırır.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f3b46aa13e492017f54e452e37eca025ecab842b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725112"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Bu arabirim, hata ayıklama bağlantı noktası üzerinde çalışan işlemi numaralandırır.

## <a name="syntax"></a>Syntax

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bir bağlantı noktasında çalışan işlemlerin listesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio, bu arabirimi edinmek için [enumprocesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugProcesses2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Bir numaralandırma dizisindeki belirtilen sayıda işlemi alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda işlemi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Bir Numaralandırıcı içindeki işlem sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, **işlem** penceresini doldurmak için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
