---
title: StartProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 994cde18cfe304add796bffa74d2a327e1c63f45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199752"
---
# <a name="startprofile"></a>StartProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`StartProfile`İşlevi, belirtilen profil oluşturma düzeyi için sayacı 1 (açık) olarak ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Level`  
  
 Performans veri koleksiyonunun uygulanabileceğini gösteren profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** Numaralandırıcılar, performans verileri koleksiyonunun uygulanabileceği üç düzeyden birini göstermek için kullanılabilir:  
  
|Sının|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Genel düzey ayarı, profil oluşturma çalıştırmasında tüm işlem ve iş parçacıklarını etkiler.|  
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen işlemin parçası olan tüm iş parçacıklarını etkiler.|  
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma düzeyi ayarı belirtilen iş parçacığını etkiler.|  
  
 `dwId`  
  
 Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısı.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:  
  
|Sının|Description|  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework Eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgileri  
 Üst bilgi: VSPerf. h içinde bildiriliyor  
  
 İçeri aktarma kitaplığı: VSPerf. lib  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek StartProfile işlev çağrısını gösterir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
