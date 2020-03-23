---
title: Özgeçmiş Profili | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3d65d5fcf8961493c2b780453f2143de788551a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778316"
---
# <a name="resumeprofile"></a>ResumeProfile
Yöntem, `ResumeProfile` belirtilen profil oluşturma düzeyi için Askıya Al/Devam sayacını belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
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
 Askıya Alma/Devam sayacının başlangıç değeri 0'dır. Askıya Alma Profili'ne yapılan her çağrı Askıya Alma/Devam sayısına 1 ekler; ResumeProfile'a her çağrı 1'i çıkarır.

 Askıya Alma/Devam sayısı 0'dan büyükolduğunda, düzeyiçin Askıya Al/Devam durumu KAPALIOLUR. Sayım 0'dan küçük veya eşit olduğunda, Askıya Alma/Devam durumu AÇILDIR.

 Başlat/Durdur durumu ve Askıya Alma/Devam durumu her ikisi de A.B.D. olduğunda, düzeyin profil oluşturma durumu A.B.D. Bir iş parçacığının profilinin atAbilmesi için iş parçacığının genel, işlem ve iş parçacığı düzeyi durumlarını niçin on olması gerekir.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Fonksiyon bilgileri
 Üstbilgi: *VSPerf.h'de* beyan edile

 İthalat kitaplığı: *VSPerf.lib*

## <a name="example"></a>Örnek
 Aşağıdaki örnekte ResumeProfile işlevi gösteriş verilmiştir. Örnek, AskProfile yöntemine çağrı nın [PROFILE_CURRENTID](../profiling/profile-currentid.md)tarafından tanımlanan aynı iş parçacığı veya işlem için yapıldığını varsayar.

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
