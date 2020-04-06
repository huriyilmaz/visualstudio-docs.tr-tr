---
title: IDebugMethodField::EnumParametreler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727190"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Yöntemin parametreleri için bir sayısallaştırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametreler
`ppParams`\
[çıkış] Parametre listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesini yönteme döndürür; aksi takdirde, parametre yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, parametre yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Her öğe, farklı parametre türlerini temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesidir. Nesnenin tam olarak ne tür bir parametreyi temsil etmesini belirlemek için her nesnedeki [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemini arayın.

 Bir parametre hem değişken adını hem de türünü içerir. Bir sınıf yönteminin ilk parametresi genellikle "bu" işaretçisidir.

 Yalnızca parametre türleri gerekiyorsa, [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
