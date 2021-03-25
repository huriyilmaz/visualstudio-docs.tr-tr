---
description: Sınıfta belirli bir arabirimin tanımlanıp tanımlanamayacağını belirler.
title: IDebugClassField::D Oesınterfaceexist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60a9a64e408f182476d6f34b19fea45f6fe8ad48
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085032"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Sınıfta belirli bir arabirimin tanımlanıp tanımlanamayacağını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parametreler
`pszInterfaceName`\
'ndaki Aranacak arabirim adını içeren bir dize.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür, arabirim yoksa S_FALSE döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, tüm arabirimlerin bir listesini alır ve listede eşleşen bir arabirim arar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
