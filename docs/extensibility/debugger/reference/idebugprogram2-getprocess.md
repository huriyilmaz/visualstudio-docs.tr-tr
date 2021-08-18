---
description: Bu programın içinde çalıştır olduğu işlemi elde.
title: IDebugProgram2::GetProcess | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 135d8e632b4cef71050db0ba326388170037e732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126550"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Bu programın içinde çalıştır olduğu işlemi elde.

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
[out] Işlemi [temsil eden IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısı (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) arabirimini uygulamadıkça, DE'nin bu yöntemi uygulaması her zaman dönmeli çünkü de hangi işlemde çalıştırdığını belirleyebildi ve bu nedenle bu yöntemin bir uygulamasını `E_NOTIMPL` karşılayamaz.

 Arabirimin uygulanması, DE'nin bir işlemi nasıl oluşturabileceklerini bilmek zorunda olduğu anlamına gelir; bu nedenle `IDebugEngineLaunch2` DE'nin [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi uygulaması hangi işlemde çalıştırdığını bilmektedir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
