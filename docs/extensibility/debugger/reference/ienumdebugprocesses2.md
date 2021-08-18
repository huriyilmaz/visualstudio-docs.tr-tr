---
description: Bu arabirim, bir hata ayıklama bağlantı noktası üzerinde çalışan işlemleri numaralar.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125523"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Bu arabirim, bir hata ayıklama bağlantı noktası üzerinde çalışan işlemleri numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası sağlayıcı, bağlantı noktası üzerinde çalışan işlemlerin listesini sağlamak için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio [arabirimi almak için EnumProcesses'i](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) çağırıyor.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugProcesses2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Bir numaralama dizisinde belirtilen sayıda işlemi alma.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Bir numaralama dizisinde belirtilen sayıda işlemi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Numaralayıcıda işlem sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, İşlemler penceresini doldurmak için **bu arabirimi** kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
