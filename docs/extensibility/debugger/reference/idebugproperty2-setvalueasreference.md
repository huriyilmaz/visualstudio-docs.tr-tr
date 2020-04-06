---
title: IDebugProperty2::SetValueAsReference | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721257"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Bu özelliğin değerini verilen başvurunun değerine ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametreler
`rgpArgs`\
[içinde] Yönetilen kod özelliği ayarlayıcısına geçirilen bir dizi bağımsız değişken. Özellik ayarlayıcısı bağımsız değişkenleri almazsa veya bu [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi böyle `rgpArgs` bir özellik ayarlayıcısına atıfta bulunmuyorsa, null değeri olmalıdır. Bu parametre genellikle null değeridir.

`dwArgCount`\
[içinde] Dizideki `rgpArgs` bağımsız değişken sayısı.

`pValue`\
[içinde] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi biçiminde, bu özelliği ayarlamak için kullanılacak değere yapılan başvuru.

`dwTimeout`\
[içinde] Milisaniye cinsinden değeri ayarlamak için ne kadar sürer. Tipik bir `INFINITE`değer. Bu, olası bir değerlendirmenin alacağı süreyi etkiler.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, genellikle aşağıdakilerden biri olan bir hata kodu döndürür:

|Hata|Açıklama|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Başvurudaki değeri ayarlama desteklenmez.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Bu özellik bir yönteme atıfta bulunduğundan, değer ayarlanamaz.|
|`E_SETVALUE_VALUE_IS_READONLY`|Değer salt okunur ve ayarlanamaz.|
|`E_NOTIMPL`|Yöntem uygulanmaz.|

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
