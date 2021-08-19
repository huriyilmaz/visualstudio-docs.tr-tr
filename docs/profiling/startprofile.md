---
title: StartProfile | Microsoft Docs
description: StartProfile işlevini ve belirtilen profil oluşturma düzeyi için sayacı 1 'e (açık) nasıl ayarlay olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0501ef7fb0e5572c08a0712efa711130d21dabe0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157241"
---
# <a name="startprofile"></a>StartProfile
İşlev, `StartProfile` belirtilen profil oluşturma düzeyi için sayacı 1 (açık) olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(
                        PROFILE_CONTROL_LEVEL Level,
                        unsigned int dwId);
```

#### <a name="parameters"></a>Parametreler
 `Level`

 Performans verisi toplamanın uygulana profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** numaralandırıcıları, performans verisi toplamanın uygulan olduğu üç düzeyden birini belirtmek için kullanılabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Genel düzey ayarı, profil oluşturma çalıştırması sırasındaki tüm işlemleri ve iş parçacıklarını etkiler.|
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen sürecin parçası olan tüm iş parçacıklarını etkiler.|
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma Düzeyi ayarı belirtilen iş parçacığını etkiler.|

 `dwId`

 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 işlevi, bir veya daha fazla **numaralama kullanarak PROFILE_COMMAND_STATUS** gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Profil oluşturma öğesi kimliği yok.|
|PROFILE_ERROR_LEVEL_NOEXIST|Belirtilen profil oluşturma düzeyi yok.|
|PROFILE_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldıken NEVER olarak ayarlanmıştır.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Profil oluşturma işlevi çağrısı, profil oluşturma düzeyi veya çağrı ve düzey birleşimi henüz uygulanmamıştır.|
|PROFILE_OK|Çağrı başarılı oldu.|

## <a name="remarks"></a>Açıklamalar
 StartProfile ve StopProfile profil oluşturma düzeyi için Başlat/Durdur durumunu kontrol edin. Başlat/Durdur varsayılan değeri 1'tir. İlk değer kayıt defterinde değiştirilebilir. StartProfile'a yapılan her çağrı Başlat/Durdur'ı 1 olarak ayarlar; StopProfile'a yapılan her çağrı bunu 0 olarak ayarlar.

 Başlat/Durdur 0'dan büyükse düzeyin Başlat/Durdur durumu ON olur. 0'dan küçük veya ona eşit olduğunda Başlat/Durdur durumu OFF olur.

 Başlatma/Durdurma durumu ve Askıya Alma/Sürdürme durumu açık olduğunda, düzeyin profil oluşturma durumu ON olur. Bir iş parçacığının profili oluşturmak için iş parçacığı için genel, işlem ve iş parçacığı düzeyi durumları AÇıK olması gerekir.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğer
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri
 Üst Bilgi: *VSPerf.h içinde bildirildi*

 İçeri aktarma kitaplığı: *VSPerf.lib*

## <a name="example"></a>Örnek
 Aşağıdaki örnek StartProfile işlev çağrısını gösterir.

```cpp
void ExerciseStartProfile()
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

    // Declare enumeration to hold return value of
    // the call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = StartProfile(
        PROFILE_THREADLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StartProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profil oluşturma API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
