---
description: Bu programın üzerinde çalıştığı işlemi alın.
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d87d863b954a9865ff3960f2f2cdd45ac40ce58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065404"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Bu programın üzerinde çalıştığı işlemi alın.

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
