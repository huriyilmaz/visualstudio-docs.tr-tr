---
title: SuspendProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b40b37c8c0ee97b5d7e0cc33773af140bd1010b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155619"
---
# <a name="suspendprofile"></a>SuspendProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SuspendProfile`Yöntemi, belirtilen profil oluşturma düzeyi Için askıya al/sürdürüm sayacını artırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
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
 Askıya alma/sürdürülme sayacının başlangıç değeri 0 ' dır. Her SuspendProfile çağrısı, askıya alma/sürdürülme sayısına 1 ekler; Her ResumeProfile çağrısı 1 ' i çıkartır.  
  
 Askıya alma/sürdürülme sayısı 0 ' dan büyükse, düzeyin askıya alma/bırakma durumu kapalı olur. Sayı 0 ' dan küçük veya buna eşit olduğunda, askıya alma/bekleme durumu açık olur.  
  
 Başlat/Durdur durumu ve askıya alma/bekleme durumu her ikisi de olduğunda, düzeyin profil oluşturma durumu açık olur. Bir iş parçacığının profili oluşturmak için, iş parçacığının genel, işlem ve iş parçacığı düzeyi durumları açık olmalıdır.  
  
## <a name="net-framework-equivalent"></a>.NET Framework Eşdeğeri  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>İşlev bilgileri  
 Üst bilgi: VSPerf. h içinde bildiriliyor  
  
 İçeri aktarma kitaplığı: VSPerf. lib  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte SuspendProfile yöntemi gösterilmektedir. Bu örnek, [PROFILE_CURRENTID](../profiling/profile-currentid.md)tarafından tanımlanan işlem veya iş parçacığı Için StartProfile 'e yapılan önceki çağrının yapıldığını varsayar.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
