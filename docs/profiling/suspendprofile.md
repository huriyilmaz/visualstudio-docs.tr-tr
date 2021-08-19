---
title: SuspendProfile | Microsoft Docs
description: SuspendProfile yönteminin belirtilen profil oluşturma düzeyi için Askıya Al/Sürdür sayacını nasıl artır aldığını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0826afe211de54723f49fa29b40fb0f91ede026f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157156"
---
# <a name="suspendprofile"></a>SuspendProfile
yöntemi, `SuspendProfile` belirtilen profil oluşturma düzeyi için Askıya Al/Sürdür sayacını artırır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
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
 Askıya Al/Sürdür sayacının ilk değeri 0'dır. SuspendProfile'a yapılan her çağrı Askıya Alma/Sürdürme sayısına 1 ekler; ResumeProfile'a yapılan her çağrı 1'i çıkarır.

 Askıya Alma/Sürdürme sayısı 0'dan büyükse, düzey için Askıya Al/Sürdür durumu OFF olur. Sayı 0'dan küçük veya 0'a eşit olduğunda Askıya Al/Sürdür durumu ON olur.

 Başlatma/Durdurma durumu ve Askıya Alma/Sürdürme durumu açık olduğunda, düzeyin profil oluşturma durumu ON olur. Bir iş parçacığının profilinin profili oluşturmak için iş parçacığının genel, işlem ve iş parçacığı düzeyi durumları açık olması gerekir.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğer
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri
 Üst Bilgi: *VSPerf.h içinde bildirildi*

 İçeri aktarma kitaplığı: *VSPerf.lib*

## <a name="example"></a>Örnek
 Aşağıdaki örnek SuspendProfile yöntemini göstermektedir. Bu örnekte, tarafından tanımlanan işlem veya iş parçacığı için startProfile'a daha önce bir çağrı [PROFILE_CURRENTID.](../profiling/profile-currentid.md)

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profil oluşturma API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
