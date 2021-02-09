---
title: 'Idebuggenericfielddefinition:: Constructörneklemesi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ab91340c0f9baf9a75e6e283d3c1158bdbea3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911120"
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
