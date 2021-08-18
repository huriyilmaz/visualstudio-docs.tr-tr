---
description: Programın özelliklerini alır.
title: 'IDebugProgram2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adac39c45a001a45d57b7e2cc5ac816ba4d6dd87
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087853"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Programın özelliklerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametreler
`ppProperty`\
dışı Programın özelliklerini temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin döndürdüğü özellikler programa özeldir. Programın birden fazla özellik döndürmesi gerekiyorsa, bu yöntem tarafından döndürülen [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi ek özelliklerin bir kapsayıcısıdır ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yönteminin çağrılması tüm özelliklerin bir listesini döndürür.

 Bir program, arabirim aracılığıyla açıklanabileceğiniz herhangi bir sayıyı ve ek özellik türünü kullanıma sunabilir `IDebugProperty2` . IDE, genel bir özellik tarayıcısı Kullanıcı arabirimi aracılığıyla ek program özelliklerini görüntüleyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
