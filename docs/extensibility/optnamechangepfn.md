---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: Kaynak denetimi eklentisinden gelen ad değişikliklerini IDE'deki kaynak IDE'ye ileten OPTNAMECHANGEPFN geri çağırma işlevini Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 15485540921f9a4dbe3ef95e0fd878eeaecc5d5a8861a3e4460999be3d3d8bb7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414109"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Bu, [SccSetOption](../extensibility/sccsetoption-function.md) çağrısında belirtilen bir geri çağırma işlevidir (seçeneği kullanılarak) ve kaynak denetimi eklentisi tarafından yapılan ad değişikliklerini IDE'ye geri `SCC_OPT_NAMECHANGEPFN` ileterek kullanılır.

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

[in] [SccSetOption'a](../extensibility/sccsetoption-function.md) önceki bir çağrıda belirtilen kullanıcı değeri (seçeneğini `SCC_OPT_USERDATA` kullanarak).

 pszOldName

[in] Dosyanın özgün adı.

 pszNewName

[in] Dosyanın yeniden adlandırıldı olduğu ad.

## <a name="return-value"></a>Döndürülen değer
 Yok.

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi işlemi sırasında bir dosya yeniden adlandırıldı ise, kaynak denetimi eklentisi bu geri arama aracılığıyla ad değişikliğini IDE'ye bildirebilirsiniz.

 IDE bu geri çağırmayı desteklemezse, belirtmek için [SccSetOption'ı](../extensibility/sccsetoption-function.md) çağırmaz. Eklenti bu geri çağırmayı desteklemezse, IDE geri çağırmayı ayarlamayı denemesi `SCC_E_OPNOTSUPPORTED` `SccSetOption` için işlevden geri döner.

## <a name="see-also"></a>Ayrıca bkz.
- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
