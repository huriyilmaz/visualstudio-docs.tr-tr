---
title: IDebugEngineLaunch2::CanTerminateProcess | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730566"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Bir işlemin sonlandırılap sonlandırılamayacağını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametreler
`pProcess`\
[içinde] Sonlandırılacak işlemi temsil eden bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür. Erişim `S_FALSE` reddedildiği için, örneğin, altyapı işlemi sonlandıramıyorsa döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem `S_OK`dönerse, bu işlemi gerçekten sonlandırmak için [Sonlandırma İşlemi](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) yöntemi çağrılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
