---
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722787"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Bu programın üzerinde çalıştığı işlemi alın.

## <a name="syntax"></a>Söz dizimi

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
dışı İşlemi temsil eden [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısı (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) arabirimini uygulamadıkça, bu yöntemin uygulamasının de uygulanması her zaman döndürmelidir, `E_NOTIMPL` çünkü bir de hangi işlemin üzerinde çalıştığını belirleyemez ve bu nedenle bu yöntemin bir uygulamasını karşılayamaz.

 Arabirimi uygulamak `IDebugEngineLaunch2` , de bir işlemin nasıl oluşturulduğunu bilmesi gerektiği anlamına gelir; bu nedenle, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi uygulamasının, içinde hangi işlemin çalıştığını biliyor olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
