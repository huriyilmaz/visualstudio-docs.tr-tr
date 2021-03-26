---
description: Bağımsız değişken türünde dizi verilen bir alan örneği oluşturur.
title: 'Idebuggenericfielddefinition:: Constructörneklemesi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4565077357678725a6601ac14c48cfce21ec9101
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063441"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Bağımsız değişken türünde dizi verilen bir alan örneği oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parametreler
`cArgs`\
'ndaki Dizideki bağımsız değişken sayısı `ppArgs` .

`ppArgs`\
'ndaki Tür bağımsız değişkenlerini içeren dizi. Tür bağımsız değişkenleri kapalı olmalıdır (genel olmayan veya tam olarak örneklenmiş genel türler).

`ppConstructedField`\
dışı Yeni alanı temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kısıtlamalar denetlenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
