---
title: SuspendProfile | Microsoft Docs
description: SuspendProfile yönteminin, belirtilen profil oluşturma düzeyi için askıya alma/bekleme sayacını nasıl artırdığı hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 728aa7c858f8321e3289f2d17e612284f8739f17
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719272"
---
# <a name="suspendprofile"></a>SuspendProfile
`SuspendProfile`Yöntemi, belirtilen profil oluşturma düzeyi Için askıya al/sürdürüm sayacını artırır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
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
 Askıya alma/sürdürülme sayacının başlangıç değeri 0 ' dır. Her SuspendProfile çağrısı, askıya alma/sürdürülme sayısına 1 ekler; Her ResumeProfile çağrısı 1 ' i çıkartır.

 Askıya alma/sürdürülme sayısı 0 ' dan büyükse, düzeyin askıya alma/bırakma durumu kapalı olur. Sayı 0 ' dan küçük veya buna eşit olduğunda, askıya alma/bekleme durumu açık olur.

 Başlat/Durdur durumu ve askıya alma/bekleme durumu her ikisi de olduğunda, düzeyin profil oluşturma durumu açık olur. Bir iş parçacığının profili oluşturmak için, iş parçacığının genel, işlem ve iş parçacığı düzeyi durumları açık olmalıdır.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri
 Üst bilgi: *VSPerf. h* içinde bildiriliyor

 İçeri aktarma kitaplığı: *VSPerf. lib*

## <a name="example"></a>Örnek
 Aşağıdaki örnekte SuspendProfile yöntemi gösterilmektedir. Bu örnek, [PROFILE_CURRENTID](../profiling/profile-currentid.md)tarafından tanımlanan işlem veya iş parçacığı Için StartProfile 'e yapılan önceki çağrının yapıldığını varsayar.

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
- [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
