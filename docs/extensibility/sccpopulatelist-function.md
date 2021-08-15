---
description: Bu işlev belirli bir kaynak denetimi komutu için dosyaların listesini günceller ve verilen tüm dosyalarda kaynak denetimi durumu sağlar.
title: SccPopulateList İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ce9ed39a90e467bb31f8272d9977406149a5b1ecdf3eecc390903ad0bf24c9e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305210"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList İşlevi
Bu işlev belirli bir kaynak denetimi komutu için dosyaların listesini günceller ve verilen tüm dosyalarda kaynak denetimi durumu sağlar.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 nCommand

[in] Dizide yer alan tüm dosyalara uygulanacak kaynak denetim `lpFileNames` komutu (olası [komutların listesi](../extensibility/command-code-enumerator.md) için bkz. Komut Kodu).

 nFiles

[in] Dizide dosya `lpFileNames` sayısı.

 lpFileNames

[in] IDE tarafından bilinen bir dosya adı dizisi.

 pfnPopulate

[in] Dosyaları eklemek ve kaldırmak için çağrılan IDE geri çağırma işlevi (ayrıntılar için [bkz. POPLISTFUNC).](../extensibility/poplistfunc.md)

 pvCallerData

[in] Değiştirilmeden geri çağırma işlevine geçirilme değeri.

 lpStatus

[in, out] Her dosyanın durum bayraklarını iade etmek için kaynak denetimi eklentisine bir dizi.

 fOptions

[in] Komut bayrakları (ayrıntılar için Bit bayrakları Belirli Komutlar Tarafından Kullanılan [Bit bayraklarının](../extensibility/bitflags-used-by-specific-commands.md) "PopulateList bayrağı" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, geçerli durumu için dosya listesini inceler. Bir dosya `pfnPopulate` ölçütüyle eşleşmezken çağıranı bildirmek için geri çağırma işlevini `nCommand` kullanır. Örneğin, komut ve listede bir dosya kullanıma alınmışsa, çağıranı bilgilendirmek `SCC_COMMAND_CHECKIN` için geri çağırma kullanılır. Bazen kaynak denetimi eklentisi komutun parçası olan diğer dosyaları bulabilir ve bunları ekleyebilir. Bu, örneğin bir Visual Basic kullanıcının projesi tarafından kullanılan ancak .bmp proje dosyasında görünmeen bir Visual Basic sağlar. Kullanıcı **IDE'de Al** komutunu seçer. IDE, kullanıcının aldırılanı düşündüğü tüm dosyaların listesini görüntüler, ancak liste gösterilmeden önce, görüntülenecek listenin güncel olduğundan emin olmak için `SccPopulateList` işlev çağrılır.

## <a name="example"></a>Örnek
 IDE, kullanıcının aldırarak elde etmek için düşündüğü dosyaların listesini derleme. Bu listeyi görüntülemeden önce işlevini çağırarak kaynak denetimi eklentisine listeden dosya ekleme ve `SccPopulateList` silme fırsatı verir. Eklenti, verilen geri çağırma işlevini çağırarak listeyi değiştiren bir işlevdir (daha fazla ayrıntı için [bkz. POPLISTFUNC).](../extensibility/poplistfunc.md)

 Eklenti, tamamlanıncaya ve işlevden dönene kadar dosyaları ekleyen ve `pfnPopulate` silen işlevini çağırmaya devam `SccPopulateList` eder. Daha sonra IDE listesini ekleyebilirsiniz. dizisi, `lpStatus` IDE tarafından geçirilen özgün listede yer alan tüm dosyaları temsil eder. Eklenti, geri çağırma işlevinin kullanımına ek olarak tüm bu dosyaların durumunu doldurur.

> [!NOTE]
> Kaynak denetimi eklentisi her zaman bu işlevden hemen dönme seçeneğine sahiptir ve listeden olduğu gibi ayrılır. Bir eklenti bu işlevi uygulayıyorsa, `SCC_CAP_POPULATELIST` [SccInitialize'a](../extensibility/sccinitialize-function.md)yapılan ilk çağrıda bitflag özelliğini ayarlayan bunu belirtebilirsiniz. Varsayılan olarak, eklenti her zaman geçirilen tüm öğelerin dosyalar olduğunu varsaymalı. Ancak, IDE parametresinde `SCC_PL_DIR` bayrağı `fOptions` ayarlarsa, geçirilen tüm öğeler dizin olarak kabul edilir. Eklentinin dizinlere ait olan tüm dosyaları eklemesi gerekir. IDE hiçbir zaman dosya ve dizinlerin karışımını geçmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [Komut Kodu](../extensibility/command-code-enumerator.md)
