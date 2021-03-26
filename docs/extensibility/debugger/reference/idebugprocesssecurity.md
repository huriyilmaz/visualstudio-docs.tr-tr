---
description: Idebugprocesssecurity, işleme bağlanan kullanıcıyı uyarmak için bir bağlantı noktası sağlayıcısı tarafından uygulanır.
title: Idebugprocesssecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7466d88be9460a2b4680fc7d14a741df9238ea0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076270"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` , işleme bağlanan kullanıcıyı uyarmak için bir bağlantı noktası sağlayıcısı tarafından uygulanır.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProcessSecurity` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Bağlantı noktası tedarikçiden Kullanıcı adını alır.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Hata ayıklama işlemine eklenen bir kullanıcıyı güvenli olmayan bir şekilde uyarır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirimi, bir uyarı göstermek ve iliştirmekte olduğunuz işlem güvenli olmadığı kabul edildiğinde kullanıcının iptal edilmesine izin vermek için uygulayın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktaları](../../../extensibility/debugger/ports.md)
- [Bağlantı Noktası Sağlayıcıları](../../../extensibility/debugger/port-suppliers.md)
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
