---
description: Bu işlev, kaynak denetimi eklentisi tarafından desteklenen ek özellikleri döndürür.
title: SccGetExtendedCapabilities İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: df8c80eb5644d00cc6130d329b9d2cb7bdf75f8c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086345"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities işlevi
Bu işlev, kaynak denetimi eklentisi tarafından desteklenen ek özellikleri döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 lSccExCaps

[in] Test sınanacak genişletilmiş bir özelliği belirten bayrak (olası bayraklar için Yetenek bayrakları'nın Genişletilmiş Yetenek [Kodu](../extensibility/capability-flags.md) tablosuna bakın).

 pbSupported

[out] Belirtilen özellik destekiliyorsa sıfır olmayan ( ) döndürür; aksi `TRUE` takdirde sıfır () `FALSE` döndürür.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Yetenek al işlemi başarıyla tamamlandı.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Bilinmeyen veya belirtilmeyen hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem isteğe bağlı olarak çağrılır; Başka bir ifadeyle, bir özelliğin test sınanmış olması gerekirse, bu özelliğin destek olup olmadığını belirlemek için bu yöntem çağrılır. Aynı anda yalnızca bir bayrak belirtilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Hata kodları](../extensibility/error-codes.md)
- [Yetenek bayrakları](../extensibility/capability-flags.md)
