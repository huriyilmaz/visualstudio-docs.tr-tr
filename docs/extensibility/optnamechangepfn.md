---
title: OPTNAMECHANGEPFN | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702246"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Bu, [SccSetOption'a](../extensibility/sccsetoption-function.md) yapılan bir çağrıda belirtilen bir `SCC_OPT_NAMECHANGEPFN`geri arama işlevidir (seçeneği kullanarak) ve kaynak denetimi eklentisi tarafından yapılan ad değişikliklerini IDE'ye geri iletmek için kullanılır.

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

[içinde] [SccSetOption'a](../extensibility/sccsetoption-function.md) yapılan önceki bir çağrıda belirtilen `SCC_OPT_USERDATA`kullanıcı değeri (seçeneği kullanarak).

 pszOldName

[içinde] Dosyanın orijinal adı.

 pszNewName

[içinde] Dosyanın adı değiştirildi.

## <a name="return-value"></a>Döndürülen değer
 Yok.

## <a name="remarks"></a>Açıklamalar
 Bir dosya nın kaynak denetim işlemi sırasında yeniden adlandırılması durumunda, kaynak denetim eklentisi bu geri arama yoluyla ad değişikliği hakkında IDE'ye bildirebilir.

 IDE bu geri aramayı desteklemiyorsa, belirtmek için [SccSetOption'ı](../extensibility/sccsetoption-function.md) aramaz. Eklenti bu geri aramayı desteklemiyorsa, IDE `SccSetOption` geri aramayı ayarlamaya çalıştığında işlevden geri döner. `SCC_E_OPNOTSUPPORTED`

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
