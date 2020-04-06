---
title: IDebugWindowsComputerPort2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718220"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Hedef bilgisayar hakkında bilgi için sorgulama sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim, oturum hata ayıklama yöneticisinin bağlantı noktası nesneleri tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugWindowsComputerPort2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Hata ayıklamanın çalıştırıldığı bilgisayar hakkındaki bilgileri alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
