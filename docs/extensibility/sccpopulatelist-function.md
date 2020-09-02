---
title: SccPopulateList Işlevi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700525"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList İşlevi
Bu işlev belirli bir kaynak denetimi komutu için bir dosya listesini güncelleştirir ve tüm verilen dosyalardaki kaynak denetimi durumunu sağlar.

## <a name="syntax"></a>Söz dizimi

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 Nyürütülen komut

'ndaki Dizideki tüm dosyalara uygulanacak kaynak denetimi komutu `lpFileNames` (olası komutların listesi için bkz. [komut kodu](../extensibility/command-code-enumerator.md) ).

 Nkarşıya

'ndaki Dizideki dosya sayısı `lpFileNames` .

 lpDosyaAdı

'ndaki IDE tarafından bilinen dosya adlarından oluşan bir dizi.

 pfnPopulate

'ndaki Dosya ekleme ve kaldırma çağrısı yapılacak IDE geri çağırma işlevi (Ayrıntılar için bkz. [Poplistfunc](../extensibility/poplistfunc.md) ).

 pvCallerData

'ndaki Geri çağırma işlevine değiştirilmeden geçirilecek değer.

 lpStatus

[in, out] Her dosya için durum bayraklarını döndürecek kaynak denetimi eklentisi için bir dizi.

 fOptions

'ndaki Komut bayrakları (Ayrıntılar için [belirli komutlar tarafından kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md) 'ın "PopulateList Flag" bölümüne bakın).

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Başarılı.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, geçerli durumu için dosya listesini inceler. `pfnPopulate`Bir dosya ile ilgili ölçütlerle eşleşmediği zaman, çağrıyı yapana bildirmek için geri çağırma işlevini kullanır `nCommand` . Örneğin, komut ise `SCC_COMMAND_CHECKIN` ve listedeki bir dosya kullanıma alınmamış ise, çağrıyı yapana bildirmek için geri çağırma kullanılır. Bazen, kaynak denetimi eklentisi, komutun parçası olabilecek diğer dosyaları bulabilir ve bunları ekleyebiliriz. Bu, örneğin, bir Visual Basic kullanıcının projesi tarafından kullanılan ancak Visual Basic proje dosyasında görünmeyen bir. bmp dosyasını kullanıma almasına izin verir. Kullanıcı IDE 'de **Al** komutunu seçer. IDE, kullanıcının alabilir olduğunu düşündüğü tüm dosyaların bir listesini görüntüler, ancak liste gösterilmeden önce, `SccPopulateList` görüntülenecek listenin güncel olduğundan emin olmak için işlev çağırılır.

## <a name="example"></a>Örnek
 IDE, kullanıcının alabilir olduğunu düşündüğü dosyaların bir listesini oluşturur. Bu listeyi görüntülemeden önce, `SccPopulateList` kaynak denetimi eklentisine, listeden dosya ekleme ve silme fırsatı vererek işlevini çağırır. Eklenti, belirtilen geri çağırma işlevini çağırarak listeyi değiştirir (daha fazla ayrıntı için bkz. [Poplistfunc](../extensibility/poplistfunc.md) ).

 Eklenti, `pfnPopulate` tamamlanana kadar dosya ekleyen ve silen işlevi çağırmaya devam eder ve sonra işlevden geri döner `SccPopulateList` . Daha sonra IDE, listesini görüntüleyebilir. `lpStatus`Dizi, IDE tarafından geçirilen özgün listedeki tüm dosyaları temsil eder. Eklenti, geri çağırma işlevini kullanmanın yanı sıra tüm bu dosyaların durumunu da doldurur.

> [!NOTE]
> Bir kaynak denetimi eklentisi her zaman bu işlevden hemen geri dönerek listeyi olduğu gibi bırakarak bir seçenek içerir. Bir eklenti bu işlevi uygularsa, bu, `SCC_CAP_POPULATELIST` [SccInitialize](../extensibility/sccinitialize-function.md)için ilk çağrıda capability bit bayrağını ayarlayarak bunu gösterebilir. Varsayılan olarak, eklenti her zaman geçirilen tüm öğelerin dosya olduğunu varsaymalıdır. Ancak, IDE, `SCC_PL_DIR` parametresindeki bayrağı ayarlarsa `fOptions` , geçirilen tüm öğeler dizin olarak değerlendirilir. Eklentinin, dizinlere ait tüm dosyaları eklemesi gerekir. IDE dosya ve dizinlerin bir karışımını hiçbir şekilde geçmeyecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [Komut Kodu](../extensibility/command-code-enumerator.md)
