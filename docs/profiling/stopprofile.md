---
title: StopProfile | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a5492d2bbd33e6b250b564532c929234d748506c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778238"
---
# <a name="stopprofile"></a>StopProfile
İşlev, `StopProfile` belirtilen profil oluşturma düzeyi için sayacı 0 (kapalı) olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametreler
 `Level`

 Performans veritoplamanın uygulanabileceği profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** sayısallaştırıcılar, performans veri toplamanın uygulanabileceği üç seviyeden birini belirtmek için kullanılabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Genel düzey ayarı profil oluşturma çalışmasındaki tüm işlemleri ve iş parçacıklarını etkiler.|
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen işlemin bir parçası olan tüm iş parçacıklarını etkiler.|
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma Düzeyi ayarı belirtilen iş parçacığı etkiler.|

 `dwId`

 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.

## <a name="property-valuereturn-value"></a>Özellik değeri/iade değeri
 İşlev, **numaralandırma PROFILE_COMMAND_STATUS** kullanarak başarı veya başarısızlığı gösterir. İade değeri aşağıdakilerden biri olabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Profil oluşturma öğesi kimliği yok.|
|PROFILE_ERROR_LEVEL_NOEXIST|Belirtilen profil oluşturma düzeyi yok.|
|PROFILE_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında NEVER olarak ayarlandı.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profil oluşturma işlevi çağrısı, profil oluşturma düzeyi veya çağrı ve düzey kombinasyonu henüz uygulanmadı.|
|PROFILE_OK|Arama başarılı oldu.|

## <a name="remarks"></a>Açıklamalar
 Profil oluşturma düzeyi için Start Profile ve StopProfile başlat/durdur durumunu denetler. Başlat/Durdur varsayılan değeri 1'dir. Başlangıç değeri kayıt defterinde değiştirilebilir. StartProfile'a her çağrı Başlat/Durdur'u 1 olarak ayarlar; StopProfile'a her çağrı 0 olarak ayarlar.

 Başlat/Durdur 0'dan büyükolduğunda, düzeyiçin Başlat/Durdur durumu A.B.D. 0'dan küçük veya eşit olduğunda, Başlat/Durdur durumu KAPALIDIR.

 Başlat/Durdur durumu ve Askıya Alma/Devam durumu her ikisi de A.B.D. olduğunda, düzeyin profil oluşturma durumu A.B.D. Bir iş parçacığının profilinin atAbilmesi için iş parçacığının genel, işlem ve iş parçacığı düzeyi durumlarını On olmalıdır.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Fonksiyon bilgileri
 Üstbilgi: VSPerf.h'de beyan edile

 İthalat kitaplığı: VSPerf.lib

## <a name="example"></a>Örnek
 Aşağıdaki örnekte StopProfile yöntemi gösteriş gösteriş. Örnek, startprofile yöntemine bir çağrı PROFILE_CURRENTID [tarafından](../profiling/profile-currentid.md)tanımlanan aynı iş parçacığı veya işlem için yapıldığını varsayar.

```cpp
void ExerciseStopProfile()
{
    // StartProfile and StopProfile control the
    // Start/Stop state for the profiling level.
    // The default initial value of Start/Stop is 1.
    // The initial value can be changed in the registry.
    // Each call to StartProfile sets Start/Stop to 1;
    // each call to StopProfile sets it to 0.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to StopProfile.
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = StopProfile(
        PROFILE_THREADLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StopProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
