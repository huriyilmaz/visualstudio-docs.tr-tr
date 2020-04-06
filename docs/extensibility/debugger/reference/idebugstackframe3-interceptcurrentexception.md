---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719484"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Geçerli özel durumu engellemek istediğinde geçerli yığın çerçevesinde hata ayıklama tarafından çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parametreler
`dwFlags`\
[içinde] Farklı eylemleri belirtir. Şu anda [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) yalnızca `IEA_INTERCEPT` INTERCEPT_EXCEPTION_ACTION değeri desteklenir ve belirtilmelidir.

`pqwCookie`\
[çıkış] Belirli bir özel durumu tanımlayan benzersiz değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

 Aşağıdakien en yaygın hata döndürür.

|Hata|Açıklama|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Geçerli özel durum engellenemez.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Geçerli yürütme çerçevesi henüz bir işleyici için aranmadı.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Bu yöntem bu çerçeve için desteklenmez.|

## <a name="remarks"></a>Açıklamalar
 Bir özel durum atıldığında, hata ayıklama, özel durum işleme işlemi sırasında önemli noktalarda çalışma saatinden itibaren denetimi kazanır. Bu önemli anlarda hata ayıklama, çerçevenin özel durumu engellemek isteyip istemediğini geçerli yığın çerçevesine sorabilir. Bu şekilde, yakalanan bir özel durum, yığın çerçevesi nin özel durum işleyicisi olmasa bile (örneğin, program kodundaki try/catch bloğu) bir yığın çerçevesi için anında bir özel durum işleyicisidir.

 Hata ayıklama, özel durum engellenmesi gerektiğini bilmek istediğinde, geçerli yığın çerçeve nesnesi üzerinde bu yöntemi çağırır. Bu yöntem, özel durum tüm ayrıntılarını işlemekten sorumludur. [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) arabirimi uygulanmazsa veya `InterceptStackException` yöntem herhangi bir hata döndürürse, hata ayıklayıcı özel durumu normal olarak işlemeye devam edin.

> [!NOTE]
> Özel durumlar yalnızca yönetilen kodda, yani debugged olan program .NET çalışma süresi altında çalışırken ele geçirilebilir. Tabii ki, üçüncü taraf dil `InterceptStackException` uygulayıcıları kendi hata ayıklama motorlarında eğer onlar seçerseniz uygulayabilirsiniz.

 Durdurma tamamlandıktan sonra, bir [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) sinyal verilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
