---
title: SccPopulateDirList Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700562"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList İşlevi
Bu işlev, inceleyecek dizinlerin listesi göz önüne alındığında, hangi dizinlerin ve (isteğe bağlı) dosyaların kaynak denetiminde depolanabilenleri belirler.

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
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 nDirs

[içinde] Dizideki dizin yollarının `lpDirPaths` sayısı.

 lpDirPaths

[içinde] İncelecek dizin yolları dizisi.

 pfnPopulate

[içinde] Her dizin yolu ve (isteğe bağlı olarak) `lpDirPaths` dosya adı için aramak için geri arama işlevi (ayrıntılar için [POPDIRLISTFUNC'a](../extensibility/popdirlistfunc.md) bakın).

 pvCallerData

[içinde] Geri arama işlevine değişmeden geçirilecek değer.

 fSeçenekler

[içinde] Dizinlerin nasıl işlenirdenetlenen değerlerin birleşimi (olası değerler için [Belirli Komutlar tarafından kullanılan Bit bayraklarının](../extensibility/bitflags-used-by-specific-commands.md) "PopulateDirList bayrakları" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|İşlemi başarıyla tamamladı.|
|SCC_E_UNKNOWNERROR|Bir hata oluşmuştur.|

## <a name="remarks"></a>Açıklamalar
 Yalnızca kaynak denetim deposunda bulunan dizinler ve (isteğe bağlı) dosya adları geri arama işlevine aktarılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Hata Kodları](../extensibility/error-codes.md)
