---
title: SccPopulateList Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700525"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList İşlevi
Bu işlev, belirli bir kaynak denetimi komutu için dosyaların listesini güncelleştirir ve verilen tüm dosyalarda kaynak denetimi durumu sağlar.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 nKomut

[içinde] `lpFileNames` Dizideki tüm dosyalara uygulanacak kaynak denetim komutu (olası komutların listesi için [Komut Kodu'na](../extensibility/command-code-enumerator.md) bakın).

 nDosyalar

[içinde] Dizideki `lpFileNames` dosya sayısı.

 lpFileNames

[içinde] IDE tarafından bilinen bir dizi dosya adı.

 pfnPopulate

[içinde] Dosyaları eklemek ve kaldırmak için aramak için IDE geri arama işlevi (ayrıntılar için [POPLISTFUNC'a](../extensibility/poplistfunc.md) bakın).

 pvCallerData

[içinde] Geri arama işlevine değişmeden geçirilecek değer.

 lpDurum

[içinde, dışarı] Kaynak denetimi eklentisi için her dosya için durum bayraklarını döndürmek için bir dizi.

 fSeçenekler

[içinde] Komut bayrakları (ayrıntılar için [Belirli Komutlar tarafından kullanılan Bit bayraklarının](../extensibility/bitflags-used-by-specific-commands.md) "Nüfus Listesi bayrağı" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, geçerli durumu için dosyaların listesini inceler. Bir dosya `pfnPopulate` `nCommand`için ölçütleri eşleştirmiyor zaman arayan bildirmek için geri arama işlevini kullanır . Örneğin, komut değilse `SCC_COMMAND_CHECKIN` ve listedeki bir dosya kullanıma alınmamışsa, geri arama arayana bildirmek için kullanılır. Bazen, kaynak denetimi eklentisi komutun bir parçası olabilecek diğer dosyaları bulabilir ve bunları ekleyebilir. Bu, örneğin, Visual Basic kullanıcısının projesi tarafından kullanılan ancak Visual Basic proje dosyasında görünmeyen bir .bmp dosyasını kullanıma sunmasına olanak tanır. Bir kullanıcı IDE'de **Get** komutunu seçer. IDE, kullanıcının alabileceğini düşündüğü tüm dosyaların listesini görüntüler, ancak liste gösterilmeden önce görüntülenecek listenin güncel olduğundan emin olmak için `SccPopulateList` işlev çağrılır.

## <a name="example"></a>Örnek
 IDE, kullanıcının alabileceğinizi düşündüğü dosyaların bir listesini oluşturur. Bu listeyi `SccPopulateList` görüntülemeden önce, işlevi çağırır ve kaynak denetimi eklentisine listeden dosya ekleme ve silme fırsatı verir. Eklenti, verilen geri arama işlevini arayarak listeyi değiştirir (daha fazla ayrıntı için [POPLISTFUNC'a](../extensibility/poplistfunc.md) bakın).

 Eklenti, tamamlanana `pfnPopulate` ve `SccPopulateList` ardından işlevden dönene kadar dosyaları ekleyen ve silen işlevi aramaya devam eder. IDE daha sonra listesini görüntüleyebilir. Dizi, `lpStatus` IDE tarafından geçirilen özgün listedeki tüm dosyaları temsil eder. Eklenti, geri arama işlevinden yararlanmaya ek olarak tüm bu dosyaların durumunu doldurur.

> [!NOTE]
> Bir kaynak denetim eklentisi her zaman listeyi olduğu gibi bırakarak bu işlevden hemen dönme seçeneğine sahiptir. Bir eklenti bu işlevi uygularsa, `SCC_CAP_POPULATELIST` [SccInitialize](../extensibility/sccinitialize-function.md)ilk çağrıda yetenek bitflag ayarlayarak bunu gösterebilir. Varsayılan olarak, eklenti her zaman geçirilen tüm öğelerin dosya olduğunu varsayalım. Ancak, IDE `SCC_PL_DIR` `fOptions` bayrağı parametrede ayarlarsa, geçirilen tüm öğeler dizin olarak kabul edilir. Eklenti, dizinlere ait tüm dosyaları eklemelidir. IDE, dosya ve dizinlerin bir karışımından asla geçmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [Komut Kodu](../extensibility/command-code-enumerator.md)
