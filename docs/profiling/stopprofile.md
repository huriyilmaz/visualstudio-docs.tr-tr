---
title: StopProfile | Microsoft Docs
description: StopProfile işlevini ve belirtilen profil oluşturma düzeyi için sayacı 0 (kapalı) olarak nasıl ayarlacağınızı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aef913543c56c1a70f6f2b26db305f9342d734c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141330"
---
# <a name="stopprofile"></a>StopProfile
`StopProfile`İşlevi, belirtilen profil oluşturma düzeyi için sayacı 0 (kapalı) olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>Parametreler
 `Level`

 Performans veri koleksiyonunun uygulanabileceğini gösteren profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** Numaralandırıcılar, performans verileri koleksiyonunun uygulanabileceği üç düzeyden birini göstermek için kullanılabilir:

|Sının|Açıklama|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Genel düzey ayarı, profil oluşturma çalıştırmasında tüm işlem ve iş parçacıklarını etkiler.|
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen işlemin parçası olan tüm iş parçacıklarını etkiler.|
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma düzeyi ayarı belirtilen iş parçacığını etkiler.|

 `dwId`

 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Sının|Açıklama|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Profil oluşturma öğesi KIMLIĞI yok.|
|PROFILE_ERROR_LEVEL_NOEXIST|Belirtilen profil oluşturma düzeyi yok.|
|PROFILE_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında hiçbir zaman olarak ayarlanmıştır.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profil oluşturma işlev çağrısı, profil oluşturma düzeyi veya çağrının ve düzeyin birleşimi henüz uygulanmadı.|
|PROFILE_OK|Çağrı başarılı oldu.|

## <a name="remarks"></a>Açıklamalar
 StartProfile ve StopProfile, profil oluşturma düzeyi için Başlat/Durdur durumunu denetler. Başlat/Durdur varsayılan değeri 1 ' dir. Başlangıç değeri kayıt defterinde değiştirilebilir. Her StartProfile çağrısı, 1 ' e başlar veya durdurulur; Her StopProfile çağrısı bunu 0 olarak ayarlar.

 Başlat/Durdur 0 ' dan büyükse, düzeyin başlangıç/durdurma durumu açık olur. 0 ' dan küçük veya buna eşit olduğunda, Başlat/Durdur durumu KAPALıDıR.

 Başlat/Durdur durumu ve askıya alma/bekleme durumu her ikisi de olduğunda, düzeyin profil oluşturma durumu açık olur. Bir iş parçacığının profili oluşturmak için, iş parçacığının genel, işlem ve iş parçacığı düzeyi durumları açık olmalıdır.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>İşlev bilgileri
 Üst bilgi: VSPerf. h içinde bildiriliyor

 İçeri aktarma kitaplığı: VSPerf. lib

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, StopProfile yöntemi gösterilmektedir. Örnek, [PROFILE_CURRENTID](../profiling/profile-currentid.md)tarafından tanımlanan aynı iş parçacığı veya Işlem Için StartProfile yöntemine yapılan çağrının yapıldığını varsayar.

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
- [Visual Studio profil oluşturucu apı başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
