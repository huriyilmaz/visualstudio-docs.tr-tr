---
title: SccPopulateList Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720869"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList İşlevi
Bu işlev belirli bir kaynak denetimi komutu için bir dosya listesini güncelleştirir ve tüm verilen dosyalardaki kaynak denetimi durumunu sağlar.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 Nyürütülen komut

'ndaki `lpFileNames` dizisindeki tüm dosyalara uygulanacak kaynak denetimi komutu (olası komutların listesi için bkz. [komut kodu](../extensibility/command-code-enumerator.md) ).

 Nkarşıya

'ndaki `lpFileNames` dizisindeki dosya sayısı.

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
 Bu işlev, geçerli durumu için dosya listesini inceler. Bir dosya `nCommand`ölçütleriyle eşleşmediği zaman, çağrıyı yapana bildirmek için `pfnPopulate` geri çağırma işlevini kullanır. Örneğin, komut `SCC_COMMAND_CHECKIN` ve listedeki bir dosya kullanıma alınmamış ise, çağrıyı yapana bildirmek için geri çağırma kullanılır. Bazen, kaynak denetimi eklentisi, komutun parçası olabilecek diğer dosyaları bulabilir ve bunları ekleyebiliriz. Bu, örneğin, bir Visual Basic kullanıcının projesi tarafından kullanılan ancak Visual Basic proje dosyasında görünmeyen bir. bmp dosyasını kullanıma almasına izin verir. Kullanıcı IDE 'de **Al** komutunu seçer. IDE, kullanıcının alabilir olduğunu düşündüğü tüm dosyaların bir listesini görüntüler, ancak liste gösterilmeden önce, görüntülenecek listenin güncel olduğundan emin olmak için `SccPopulateList` işlevi çağırılır.

## <a name="example"></a>Örnek
 IDE, kullanıcının alabilir olduğunu düşündüğü dosyaların bir listesini oluşturur. Bu listeyi görüntülemeden önce, kaynak denetim eklentisine, listeden dosya ekleme ve silme fırsatı vererek `SccPopulateList` işlevini çağırır. Eklenti, belirtilen geri çağırma işlevini çağırarak listeyi değiştirir (daha fazla ayrıntı için bkz. [Poplistfunc](../extensibility/poplistfunc.md) ).

 Eklenti, tamamlanana kadar dosya ekleyen ve silen `pfnPopulate` işlevini çağırmaya devam eder ve sonra `SccPopulateList` işlevinden geri döner. Daha sonra IDE, listesini görüntüleyebilir. `lpStatus` dizisi, IDE tarafından geçirilen özgün listedeki tüm dosyaları temsil eder. Eklenti, geri çağırma işlevini kullanmanın yanı sıra tüm bu dosyaların durumunu da doldurur.

> [!NOTE]
> Bir kaynak denetimi eklentisi her zaman bu işlevden hemen geri dönerek listeyi olduğu gibi bırakarak bir seçenek içerir. Bir eklenti bu işlevi uygularsa, bu, [SccInitialize](../extensibility/sccinitialize-function.md)'a yapılan ilk çağrıda `SCC_CAP_POPULATELIST` capability bit bayrağını ayarlayarak bunu gösterebilir. Varsayılan olarak, eklenti her zaman geçirilen tüm öğelerin dosya olduğunu varsaymalıdır. Ancak, IDE `fOptions` parametresinde `SCC_PL_DIR` bayrağını ayarlarsa, geçirilen tüm öğeler dizin olarak kabul edilir. Eklentinin, dizinlere ait tüm dosyaları eklemesi gerekir. IDE dosya ve dizinlerin bir karışımını hiçbir şekilde geçmeyecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
- [Komut Kodu](../extensibility/command-code-enumerator.md)