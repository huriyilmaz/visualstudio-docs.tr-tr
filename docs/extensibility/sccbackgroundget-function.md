---
description: Bu işlev, kullanıcı etkileşimi olmadan belirtilen dosyaların her biri kaynak denetiminden alınır.
title: SccBackgroundGet İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f010aa2ba214004422048513cea92adf67d62c69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144632"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet işlevi
Bu işlev, kullanıcı etkileşimi olmadan belirtilen dosyaların her biri kaynak denetiminden alınır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 nFiles

[in] Dizide belirtilen dosya `lpFileNames` sayısı.

 lpFileNames

[in, out] Alınarak alınan dosyaların adları dizisi.

> [!NOTE]
> Adların tam yerel dosya adları olması gerekir.

 Dwflags

[in] Komut bayrakları ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

[in] Bu işlemle ilişkili benzersiz bir değer.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_E_BACKGROUNDGETINPROGRESS|Bir arka plan alma işlemi zaten devam ediyor (kaynak denetimi eklentisi bunu yalnızca eşzamanlı toplu işlemleri desteklemezse bunu iade eder).|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev her zaman kaynak denetimi eklentiyi yükten farklı bir iş parçacığında çağrılır. Bu işlevin, yapılana kadar geri dönmesi beklenmmektedir; ancak, hepsi aynı anda birden çok dosya listesiyle birden çok kez çağrılabilirsiniz.

 bağımsız değişkeninin `dwFlags` kullanımı [SccGet ile aynıdır.](../extensibility/sccget-function.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
