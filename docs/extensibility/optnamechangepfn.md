---
title: SEÇENEKADı < PFN | Microsoft Docs
description: Kaynak denetim eklentisinden Visual Studio IDE 'ye olan ad değişikliklerine iletişim kuran SEÇENEKNAMECHANGEPFN callback işlevi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e583c7e19fb6123da06d0ee525abe9c573d8d788
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922880"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Bu, [SccSetOption](../extensibility/sccsetoption-function.md) (kullanma seçeneği) çağrısında belirtilen bir geri çağırma işlevidir `SCC_OPT_NAMECHANGEPFN` ve kaynak denetimi eklentisi tarafından YAPıLAN ad değişikliklerini IDE 'ye geri bildirmek için kullanılır.

## <a name="signature"></a>İmza

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametreler
 pvCallerData

'ndaki Daha önceki bir [SccSetOption](../extensibility/sccsetoption-function.md) çağrısında belirtilen kullanıcı değeri (using seçeneği `SCC_OPT_USERDATA` ).

 pszOldName

'ndaki Dosyanın özgün adı.

 Pszyeniad

'ndaki Dosyanın yeniden adlandırıldığını adı.

## <a name="return-value"></a>Döndürülen değer
 Yok.

## <a name="remarks"></a>Açıklamalar
 Kaynak denetim işlemi sırasında bir dosya yeniden adlandırılırsa, kaynak denetimi eklentisi bu geri çağırma yoluyla ad değişikliğine ilişkin IDE 'ye bildirimde bulunabilir.

 IDE bu geri çağırma işlemini desteklemiyorsa, belirtmek için [SccSetOption](../extensibility/sccsetoption-function.md) çağrısı yapmaz. Eklenti bu geri çağırma işlemini desteklemiyorsa, `SCC_E_OPNOTSUPPORTED` `SccSetOption` IDE geri aramayı ayarlamaya çalıştığında işlevinden geri döner.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
