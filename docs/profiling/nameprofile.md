---
title: İsim Profili | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9f0c9a3259186e1581a4673cdc18d1554e92b3c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778498"
---
# <a name="nameprofile"></a>NameProfile
İşlev, `NameProfile` belirtilen işlem veya iş parçacığına bir dize atar.

 NameProfile API yalnızca enstrümantasyon profilleme için kullanılabilir. NameProfile API profil oluşturma örneklemesi için desteklenmez.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametreler
 `pszName`

 Profil oluşturma öğesinin adı. Bir ad geçersizdir (şu durumlarda NameProfileA return NAME_ERROR_INVALID_NAME ile sonuçlanır)

- NameProfileA'ya geçen işaretçi NULL değeridir

- pszName'nin dize verileri bir sayı ile başlar

- pszName dize verileri bir boşluk içerir

- pszName'nin dize verileri aşağıdaki karakterlerden herhangi birini içerir: ,;. '~!@#$/^{}&*()=[] \\&#124;?/<>

  `Level`

  Performans veritoplamanın uygulanabileceği profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** değerleri, performans veritoplamanın uygulanabileceği üç düzeyden birini belirtmek için kullanılabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Genel düzey ayarı profil oluşturma çalışmasındaki tüm işlemleri ve iş parçacıklarını etkiler.|
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen işlemin bir parçası olan tüm iş parçacıklarını etkiler.|
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma Düzeyi ayarı belirtilen iş parçacığı etkiler.|

 `dwId`

 Profil oluşturma düzeyi tanımlayıcısı. Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısını kullanın.

## <a name="property-valuereturn-value"></a>Özellik değeri/iade değeri
 İşlev, **numaralandırma PROFILE_COMMAND_STATUS** kullanarak başarı veya başarısızlığı gösterir. İade değeri aşağıdakilerden biri olabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Belirtilen profil oluşturma öğesi yok.|
|NAME_ERROR_INVALID_NAME|Ad geçersiz.|
|NAME_ERROR_LEVEL_NOEXIST|Belirtilen profil düzeyi yok.|
|NAME_ERROR_NO_SUPPORT|Belirtilen işlem desteklenmiyor.|
|NAME_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek kullanılamadı.|
|NAME_ERROR_REDEFINITION|Profil öğesine zaten bir ad atandı. Bu işlevdeki ad yoksayılır.|
|NAME_ERROR_TEXTTRUNCATED|Ad metni null karakteri de dahil olmak üzere 32 karakteri aştı ve bu nedenle kesildi.|
|NAME_OK|Ad başarıyla kaydedildi.|

## <a name="remarks"></a>Açıklamalar
 Her işlem veya iş parçacığına yalnızca bir ad atanabilir. Bir profil oluşturma öğesi seçildikten sonra, bu öğe için NameProfile sonraki çağrılar yoksayılır.

 Aynı ad farklı iş parçacıklarına veya işlemlere verilirse, rapor bu ada sahip o düzeydeki tüm öğelerden veriler içerir.

 Geçerli işlem den başka bir işlem veya iş parçacığı belirtirseniz, adını vermeden önce başharfe büründin ve çalışmaya başladığından emin olmalısınız. Aksi takdirde, NameProfile yöntemi başarısız olur.

> [!IMPORTANT]
> CreateProcess() ve CreateThread() API işlevleri iş parçacığı veya işlem başharfe atılmadan önce geri dönebilir.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Fonksiyon bilgileri

|||
|-|-|
|**Üst bilgi**|*VSPerf.h* ekle|
|**Kitaplığı**|*VSPerf.lib* kullanın|
|**Unicode**|(Unicode) ve `NameProfileW` `NameProfileA` (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod NameProfile işlev çağrısını gösterir. Örnek, kodun ANSI etkin işlevini çağırıp çağırmadığını belirlemek için Win32 dize makrolarının ve ANSI için derleyici ayarlarının kullanımını varsayar.

```cpp
void ExerciseNameProfile()
{
    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Create and initialize variables to pass to
    // ExerciseNameProfile.  The value of this
    // parameter is based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variable is assigned an arbitrary value.
    TCHAR * profileName = TEXT("ExerciseNameProfile");

    // Declare enumeration to hold result of call to
    // ExerciseNameProfle.
    PROFILE_COMMAND_STATUS nameResult;

    nameResult =  NameProfile(
        profileName,
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("NameProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, nameResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
