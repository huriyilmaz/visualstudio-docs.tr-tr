---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352018e50b955ed414af974bc21b62775fd55f53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728256"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Bir dizi tür bağımsız değişkeni verilen bir alan örneği oluşturuyor.

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
[içinde] `ppArgs` Dizideki bağımsız değişken sayısı.

`ppArgs`\
[içinde] Tür bağımsız değişkenlerini içeren dizi. Tür bağımsız değişkenleri kapalı türleri (genel olmayan veya tamamen anında genel leştirilmiş genel).

`ppConstructedField`\
[çıkış] Yeni alanı temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kısıtlamalar denetlenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
