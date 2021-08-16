---
description: Bu yöntem bir alanın kapsayıcısı alır.
title: IDebugField::GetContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e87248314a97301fb49a8f4c4fef7db1a44f3e9d4eca7a84b58ea139ef12d188
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389884"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Bu yöntem bir alanın kapsayıcısı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Parametreler
`ppContainerField`\
[out] [Kapsayıcıyı IDebugContainerField arabirimiyle temsil edilen şekilde](../../../extensibility/debugger/reference/idebugcontainerfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu alanda bir kapsayıcı yoksa döndürülen değer `ppContainerField` null değer olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
