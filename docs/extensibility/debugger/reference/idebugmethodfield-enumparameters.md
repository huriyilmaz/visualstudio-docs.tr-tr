---
description: Metodun parametreleri için bir Numaralandırıcı oluşturur.
title: 'IDebugMethodField:: Trmparameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c1b00ee241f420d7c96fa27a5a02e17ab244009
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138087"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Metodun parametreleri için bir Numaralandırıcı oluşturur.

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
dışı Yönteme parametre listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür; Aksi takdirde, parametre yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür veya hiçbir parametre yoksa S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Her öğe, farklı parametre türlerini temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesidir. Nesnenin tam olarak ne tür bir parametre temsil ettiğini belirlemek için her nesne üzerinde [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemini çağırın.

 Bir parametre hem değişken adını hem de türünü içerir. Bir sınıf yöntemine ilk parametre genellikle "This" işaretçisidir.

 Yalnızca parametre türleri gerekliyse, [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
