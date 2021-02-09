---
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
ms.openlocfilehash: b5151d337618409970b61e515cd4428467a7fe25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930349"
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
