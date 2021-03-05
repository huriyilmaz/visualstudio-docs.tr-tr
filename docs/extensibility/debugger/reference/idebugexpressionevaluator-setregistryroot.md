---
description: Bu yöntem kayıt defteri kökünü ayarlar.
title: 'Idebugexpressiondeğerlendirici:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b900817a5025b0d523f8d3bb3237a1b10cc3a6a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152409"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Bu yöntem kayıt defteri kökünü ayarlar. Yan yana hata ayıklama için kullanılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

## <a name="parameters"></a>Parametreler
`ustrRegistryRoot`\
'ndaki Yeni kayıt defteri kökü.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belirtilen kayıt defteri kökü, genellikle ifade değerlendirici ilk kez başlatıldığında ayarlanır ve Visual Studio 'nun belirli bir sürümü için (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x*. *y* bir sürüm numarasıdır) kayıt defteri anahtarını işaret eder.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
