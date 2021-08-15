---
description: yöntemini içeren nesnenin bu (Visual Basic) işaretçisini alır.
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 382b230e580ac09f81a3c23a3308c5b6c844fbcf04bb89dcb240001f7759b98f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433729"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
yöntemini `this` içeren `Me` nesnenin () [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] işaretçisini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametreler
`ppClass`\
[out] "Bu" işaretçisini temsil eden bir [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Nesne odaklı dillerde genellikle bir sınıfın geçerli örneği için örtük bir işaretçi vardır. Bu, `this` C#/C++ ve içinde olarak `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] bilinir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
