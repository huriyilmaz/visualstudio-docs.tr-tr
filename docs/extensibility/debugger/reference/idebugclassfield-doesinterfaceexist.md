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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173474"
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
