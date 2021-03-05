---
description: Idebugprocesssecurity, işleme bağlanan kullanıcıyı uyarmak için bir bağlantı noktası sağlayıcısı tarafından uygulanır.
title: Idebugprocesssecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5e2ca72cc3d9c1d204c6fb1f90ccc9b03060cff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166105"
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
