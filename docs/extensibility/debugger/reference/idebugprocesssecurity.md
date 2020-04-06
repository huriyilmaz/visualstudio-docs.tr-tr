---
title: IDebugProcessSecurity | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723195"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`bir bağlantı noktası tedarikçisi tarafından, kullanıcıyı sürece iliştirmanın güvenli olmadığı konusunda uyarmak için uygulanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProcessSecurity`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Kullanıcı adını bağlantı noktası tedarikçisinden alır.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Hata ayıklama işlemine eklemenin güvenli olmadığı konusunda kullanıcıyı uyarır.|

## <a name="remarks"></a>Açıklamalar
 Bir uyarı göstermek ve iliştirdiğiniz işlem güvenli olarak kabul edilebiliyorsa kullanıcının iptal etmesine izin vermek için bu arabirimi uygulayın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı Noktaları](../../../extensibility/debugger/ports.md)
- [Bağlantı Noktası Sağlayıcıları](../../../extensibility/debugger/port-suppliers.md)
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
