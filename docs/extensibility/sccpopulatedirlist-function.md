---
description: Bu işlev, hangi dizinlerin ve (isteğe bağlı olarak) dosyaların kaynak denetiminde depolandığına ve incelenecek dizinlerin bir listesine sahip olduğunu belirler.
title: SccPopulateDirList İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d96bcef9d710833b63af04727193d3218767c407b4ab35021274ba336a062b77
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259935"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList İşlevi
Bu işlev, hangi dizinlerin ve (isteğe bağlı olarak) dosyaların kaynak denetiminde depolandığına ve incelenecek dizinlerin bir listesine sahip olduğunu belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parametreler
 Pcontext

[in] Kaynak denetimi eklentisi bağlam işaretçisi.

 nDirs

[in] Dizide dizin yolu `lpDirPaths` sayısı.

 lpDirPaths

[in] İncelenecek dizin yolları dizisi.

 pfnPopulate

[in] her dizin yolu ve (isteğe bağlı) dosya adı için çağrısı yapmak için callback işlevi (ayrıntılar için `lpDirPaths` bkz. [POPDIRLISTFUNC).](../extensibility/popdirlistfunc.md)

 pvCallerData

[in] Değiştirilmeden geri çağırma işlevine geçirilme değeri.

 fOptions

[in] Dizinlerin nasıl işlenmeyi kontrol edecek değerlerin birleşimi (olası değerler için Belirli Komutlar Tarafından Kullanılan [Bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md) bölümünün "PopulateDirList bayrakları" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_E_UNKNOWNERROR|Bir hata oluşmuştur.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca kaynak denetim deposundaki dizinler ve (isteğe bağlı olarak) dosya adları geri çağırma işlevine geçirildi.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)
