---
description: IDebugProcessSecurity, bir bağlantı noktası sağlayıcı tarafından, kullanıcıya işleme eklemenin güvenli olduğu konusunda uyarma için uygulanır.
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e97d498abbd7cbc650a0438a96570c172e5cf1d48031c92f8bef7b09de8f1860
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338897"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` , bir bağlantı noktası sağlayıcı tarafından, kullanıcıya işleme eklemenin güvenli olmayan bir şey olduğu konusunda uyarma için uygulanır.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProcessSecurity` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Bağlantı noktası sağlayıcıdan kullanıcı adını alır.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Bir kullanıcıya hata ayıklama işlemi eklemenin güvenli olmayan olduğunu belirtir.|

## <a name="remarks"></a>Açıklamalar
 Bir uyarı göstermek ve eklemekte olduğunuz işlem güvenli kabul edilirse kullanıcının iptal sınayabilecek şekilde bu arabirimi kullanın.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktaları](../../../extensibility/debugger/ports.md)
- [Bağlantı Noktası Sağlayıcıları](../../../extensibility/debugger/port-suppliers.md)
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
