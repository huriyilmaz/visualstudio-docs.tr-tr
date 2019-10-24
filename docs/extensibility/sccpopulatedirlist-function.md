---
title: SccPopulateDirList Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720890"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList İşlevi
Bu işlev, incelenecek dizinlerin listesi verildiğinde, kaynak denetiminde hangi dizinlerin ve (isteğe bağlı) dosyaların depolandığını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parametreler
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 nDirs

'ndaki `lpDirPaths` dizisindeki Dizin yollarının sayısı.

 lpDirPaths

'ndaki İncelenecek dizin yolları dizisi.

 pfnPopulate

'ndaki Her dizin yolunu ve (isteğe bağlı) `lpDirPaths` dosya adını çağırmak için geri çağırma işlevi (Ayrıntılar için bkz. [Popdirlistfunc](../extensibility/popdirlistfunc.md) ).

 pvCallerData

'ndaki Geri çağırma işlevine değiştirilmeden geçirilecek değer.

 fOptions

'ndaki Dizinlerin nasıl işlendiğini denetleyen değerlerin bir birleşimi (olası değerler için [belirli komutlar tarafından kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md) 'ın "PopulateDirList Flags" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlem başarıyla tamamlandı.|
|SCC_E_UNKNOWNERROR|Bir hata oluşmuştur.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca kaynak denetim deposundaki dizinler ve (isteğe bağlı) dosya adları geri çağırma işlevine geçirilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)