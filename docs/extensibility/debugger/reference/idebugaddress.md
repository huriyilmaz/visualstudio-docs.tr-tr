---
title: IDebugAddress | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736599"
---
# <a name="idebugaddress"></a>IDebugAddress
Bu arabirim bir öğenin adresini temsil eder. Sembol işleyicisi tarafından döndürülür.

## <a name="syntax"></a>Sözdizimi

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir sembol sağlayıcı, bir nesnenin adresini temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Birçok arabirimdeki birçok yöntem bu arabirimi döndürer.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Bir nesneyi ve konumunu açıklayan [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) bir yapı alır.|

## <a name="remarks"></a>Açıklamalar
 Sembol sağlayıcı, bu arabirimi bir nesneyi ve belirli bir kapsamdaki konumunu (örneğin, işlev, yöntem veya sınıf) temsil edecek şekilde döndürür. Bu arabirim döndürülür ve sembol sağlayıcı ve ifade değerlendiricinin çeşitli yöntemlerine geçirilir. Normalde, sembol sağlayıcı bu arabirimin içeriğini yorumlaması gereken tek varlıktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: sh.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
