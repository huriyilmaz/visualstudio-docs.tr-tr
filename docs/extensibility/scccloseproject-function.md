---
title: SccCloseProject Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4a54193b23015135b6112655fe48d79d3de74e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943159"
---
# <a name="scccloseproject-function"></a>SccCloseProject işlevi
Bu işlev, belirli bir oturumun sonuna işaret eden bir projeyi kapatır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametreler
 Kaynak denetimi eklentisi bağlam yapısını pvContext.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Proje başarıyla kapatıldı.|
|SCC_E_PROJNOTOPEN|Şu anda açık proje yok.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 [SccOpenProject](../extensibility/sccopenproject-function.md) her zaman bu işlevden önce çağırılır. Daha sonra bu işleve yapılan bir çağrı, sonra, `SccOpenProject` kaynak denetim sistemine olan bağlantıyı tamamen sonlandıran işlev veya [Sccunınitialize](../extensibility/sccuninitialize-function.md)çağrısı tarafından izlenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
