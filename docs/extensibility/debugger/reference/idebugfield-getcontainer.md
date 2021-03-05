---
description: Bu yöntem bir alanın kapsayıcısını alır.
title: 'IDebugField:: GetContainer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39be9de82e6356b16562ca4b45ea67bb40e3764f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152006"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Bu yöntem bir alanın kapsayıcısını alır.

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
dışı [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimi tarafından temsil edilen kapsayıcıyı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu alanda bir kapsayıcı yoksa, döndürülen `ppContainerField` değer null olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
