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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42864fa7d4a1250f03a797adf768472db5ae2c02
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138711"
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
 belirtilen kayıt defteri kökü genellikle ifade değerlendirici ilk kez başlatıldığında ayarlanır ve belirli bir Visual Studio için kayıt defteri anahtarını işaret eder HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio(x \\  *. y* bir sürüm numarasıdır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
