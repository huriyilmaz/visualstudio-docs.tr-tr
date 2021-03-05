---
description: Yakalanamayan bir özel durum işlenirken çağırılır.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70fb92c20eab3700043a11f8544896bbbce3b7c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172538"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Yakalanamayan bir özel durum işlenirken çağırılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parametreler
`pqwCookie`\
dışı Yakalanamayan özel durumla ilişkili benzersiz değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) yöntemi, ele geçirilebilecek bir özel durumun işlenmesini tamamladıktan sonra, [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) olayını gönderir. İşleyici `GetInterceptCookie` yöntemini özel durumla ilişkili benzersiz değeri almak için kullanabilir (yönteme geçirilen değer aynı değer `InterceptCurrentException` ).

## <a name="see-also"></a>Ayrıca bkz.
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
