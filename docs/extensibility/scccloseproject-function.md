---
description: Bu işlev, belirli bir oturumun sonuna işaret eden bir projeyi kapatır.
title: SccCloseProject Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 804afa6f8bdf0bd02ea25ba2fb4639048d2d5bf0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144502"
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
