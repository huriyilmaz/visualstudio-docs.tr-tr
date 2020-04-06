---
title: IDebugProgram2::GetProcess | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722787"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Bu programın yürüttüğü işlemi alın.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametreler
`ppProcess`\
[çıkış] İşlemi temsil eden [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) arabirimini uygulamadığı sürece, de'nin bu yöntemin uygulanması her zaman geri dönmelidir, `E_NOTIMPL` çünkü de hangi işlemde çalıştığını belirleyemez ve bu nedenle bu yöntemin uygulanmasını karşılayamaz.

 `IDebugEngineLaunch2` Arabirimi uygulamak, DE'nin bir işlem oluşturmayı bilmesi gerektiği anlamına gelir; bu nedenle, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminin DE uygulaması hangi işlemde çalıştığını bilmek mümkün.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
