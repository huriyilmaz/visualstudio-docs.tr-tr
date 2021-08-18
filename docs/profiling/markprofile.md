---
title: MarkProfile | Microsoft Docs
description: MarkProfile yöntemi, .vsp dosyasına bir profil işareti ekler. İşaretin eklenmek için MarkProfile işlevini içeren iş parçacığı için profil oluşturma AÇıK olması gerekir.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149682"
---
# <a name="markprofile"></a>MarkProfile
yöntemi, `MarkProfile` içine bir profil işareti ekler.*vsp* dosyası. İşaretin eklenmesi için işlevi içeren iş parçacığı için profil `MarkProfile` oluşturma AÇıK olması gerekir.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametreler
 `lMarker`

 Eklanacak işaretçi. İşaretçi 0'dan (sıfır) büyük veya ona eşit olmalıdır.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 işlevi, bir veya daha fazla numaralama **kullanarak PROFILE_COMMAND_STATUS** olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|parametresi 0'dan küçük veya 0'a eşittir. Bu değerler ayrılmıştır. İşaret ve açıklama kayıtlı değil.|
|MARK_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldıken NEVER olarak ayarlanmıştır. İşaret ve açıklama kayıtlı değil.|
|MARK_ERROR_MODE_OFF|İşlev çağrıldıken profil oluşturma modu OFF olarak ayarlanmıştır. İşaret ve açıklama kayıtlı değil.|
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işaret desteği yoktur. İşaret ve açıklama kayıtlı değil.|
|MARK_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek kullanılamıyor. İşaret ve açıklama kayıtlı değil.|
|MARK_TEXTTOOLONG|Dize en fazla 256 karakteri aşıyor. Açıklama dizesi kesilir ve işaret ve açıklama kaydedilir.|
|MARK_OK|MARK_OK başarılı olduğunu belirtmek için geri döndürülür.|

## <a name="remarks"></a>Açıklamalar
 İşaret değeri içine eklenir. MarkProfile işlevini içeren iş parçacığı profili ediliyorsa, kod her çalıştırıldında *vsp* dosyası. MarkProfile'ı birden çok kez çağırarak.

 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığına eklenen profil işareti, içinde herhangi bir iş parçacığında bir veri kesiminin başlangıcını veya sonunu işaretlemek için kullanılabilir. *vsp* dosyası.

 Mark komutuyla veya API işlevleriyle (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve açıklamalar olduğunda, işaret profili işlevini içeren iş parçacığının profil oluşturma durumu açık olması gerekir.

> [!IMPORTANT]
> MarkProfile yöntemi yalnızca ölçüm aracı profili oluşturma ile kullanılmalıdır.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğer
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri
 Üst Bilgi: *VSPerf.h içinde bildirildi*

 İçeri aktarma kitaplığı: *VSPerf.lib*

## <a name="example"></a>Örnek
 Aşağıdaki kod, MarkProfile işlevini gösterir.

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
- [Visual Studio profil oluşturma API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
