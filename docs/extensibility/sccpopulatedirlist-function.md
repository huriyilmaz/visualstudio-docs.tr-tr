---
title: SccPopulateDirList Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eac3973bf28a14340b720a51fc291b914822f3d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836923"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList İşlevi
Bu işlev, incelenecek dizinlerin listesi verildiğinde, kaynak denetiminde hangi dizinlerin ve (isteğe bağlı) dosyaların depolandığını belirler.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.

 nDirs

'ndaki Dizideki Dizin yollarının sayısı `lpDirPaths` .

 lpDirPaths

'ndaki İncelenecek dizin yolları dizisi.

 pfnPopulate

'ndaki İçindeki her dizin yolunu ve (isteğe bağlı) dosya adını çağırmak için geri çağırma işlevi `lpDirPaths` (Ayrıntılar için bkz. [Popdirlistfunc](../extensibility/popdirlistfunc.md) ).

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
