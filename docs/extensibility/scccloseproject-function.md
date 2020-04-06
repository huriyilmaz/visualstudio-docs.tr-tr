---
title: SccCloseProject Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701055"
---
# <a name="scccloseproject-function"></a>SccCloseProject fonksiyonu
Bu işlev, belirli bir oturumun sonunu işaretleyerek projeyi kapatır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametreler
 pvContext Kaynak denetimi eklentisi bağlam yapısı.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Proje başarıyla kapatıldı.|
|SCC_E_PROJNOTOPEN|Şu anda açık proje yok.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 [SccOpenProject](../extensibility/sccopenproject-function.md) her zaman bu işlevden önce çağrılır. Bu işleve yapılan bir çağrı, daha `SccOpenProject` sonra kaynak denetim sistemine olan bağlantıyı tamamen sona erdirebilen işlev veya [SccUninitialize'ye](../extensibility/sccuninitialize-function.md)yapılan bir çağrı yla takip edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
