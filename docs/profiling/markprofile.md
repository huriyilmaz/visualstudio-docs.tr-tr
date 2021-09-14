---
title: MarkProfile | Microsoft Docs
description: MarkProfile yöntemi. vsp dosyasına bir profil işareti ekler. MarkProfile işlevini içeren iş parçacığının profil oluşturma, eklenecek işaret için açık olmalıdır.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d8c1f089f96457c25bad703de40311000eaa65fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726828"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile`Yöntemi içine bir profil işareti ekler.*VSP* dosyası. Eklenecek işaret için işlevi içeren iş parçacığının profil oluşturma `MarkProfile` açık olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametreler
 `lMarker`

 Eklenecek işaretleyici. İşaretleyici 0 ' dan büyük veya buna eşit (sıfır) olmalıdır.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Sının|Description|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametre 0 ' dan küçük veya buna eşit. Bu değerler ayrılmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında hiçbir zaman olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_OFF|İşlev çağrıldığında profil oluşturma modu OFF olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işaret desteği yok. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek yoktu. İşaret ve açıklama kaydedilmez.|
|MARK_TEXTTOOLONG|Dize en fazla 256 karakter sınırını aşıyor. Açıklama dizesi kesilir ve işaret ve açıklama kaydedilir.|
|MARK_OK|Başarıyı göstermek için MARK_OK döndürülür.|

## <a name="remarks"></a>Açıklamalar
 İşaret değeri öğesine eklenir. MarkProfile işlevini içeren iş parçacığı profili oluşturulurken kod her çalıştığında *VSP* dosyası. MarkProfile ' i birden çok kez çağırabilirsiniz.

 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığında yerleştirilen bir profil işareti, içindeki herhangi bir iş parçacığında bir veri segmentinin başlangıcını veya sonunu işaretlemek için kullanılabilir. *VSP* dosyası.

 Mark komutuyla veya API işlevleriyle (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve açıklamalar olduğunda, işaret profili işlevini içeren iş parçacığının profil oluşturma durumu açık olmalıdır.

> [!IMPORTANT]
> MarkProfile yöntemi yalnızca izleme profili oluşturma ile birlikte kullanılmalıdır.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri
 Üst bilgi: *VSPerf. h* içinde bildiriliyor

 İçeri aktarma kitaplığı: *VSPerf. lib*

## <a name="example"></a>Örnek
 Aşağıdaki kod MarkProfile işlevini gösterir.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profil oluşturucu apı başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
