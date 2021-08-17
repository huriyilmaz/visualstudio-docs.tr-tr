---
title: NameProfile | Microsoft Docs
description: NameProfile işlevinin belirtilen işlem veya iş parçacığına bir dize atamasını öğrenin. Ayrıca, NameProfile API yalnızca izleme profili oluşturma için kullanılabilir.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa0720ee249c8bcb07306282d8ef11458391b23ef1a07db0a3cbabd53da16db6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442131"
---
# <a name="nameprofile"></a>NameProfile
`NameProfile`İşlevi belirtilen işlem veya iş parçacığına bir dize atar.

 NameProfile API yalnızca izleme profili oluşturma için kullanılabilir. NameProfile API 'SI örnekleme profili oluşturma için desteklenmiyor.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Parametreler
 `pszName`

 Profil oluşturma öğesinin adı. Ad geçersiz (NameProfileA Return NAME_ERROR_INVALID_NAME ile sonuçlanır):

- NameProfileA 'ya geçirilen işaretçi NULL bir değer

- PszName dize verileri bir sayıyla başlar

- PszName dize verilerinde bir boşluk var

- PszName dize verileri şu karakterlerden herhangi birini içerir:,;. ' ~! @ # $% ^& * () = [] {}&#124;\\ ?/<>

  `Level`

  Performans veri koleksiyonunun uygulanabileceğini gösteren profil düzeyini gösterir. Aşağıdaki **PROFILE_CONTROL_LEVEL** değerleri, performans verileri koleksiyonunun uygulanabileceği üç düzeyden birini göstermek için kullanılabilir:

|Sının|Açıklama|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Genel düzey ayarı, profil oluşturma çalıştırmasında tüm işlem ve iş parçacıklarını etkiler.|
|PROFILE_PROCESSLEVEL|İşlem düzeyi ayarı, belirtilen işlemin parçası olan tüm iş parçacıklarını etkiler.|
|PROFILE_THREADLEVEL|İş parçacığı profil oluşturma düzeyi ayarı belirtilen iş parçacığını etkiler.|

 `dwId`

 Profil oluşturma düzeyi tanımlayıcısı. Sistem tarafından oluşturulan işlem veya iş parçacığı tanımlayıcısını kullanın.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Sının|Açıklama|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Belirtilen profil oluşturma öğesi yok.|
|NAME_ERROR_INVALID_NAME|Ad geçersiz.|
|NAME_ERROR_LEVEL_NOEXIST|Belirtilen profil düzeyi yok.|
|NAME_ERROR_NO_SUPPORT|Belirtilen işlem desteklenmiyor.|
|NAME_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek yoktu.|
|NAME_ERROR_REDEFINITION|Profil öğesine zaten bir ad atandı. Bu işlevdeki ad yoksayıldı.|
|NAME_ERROR_TEXTTRUNCATED|Ad metni null karakter dahil 32 karakteri aştı ve bu nedenle kesildi.|
|NAME_OK|Ad başarıyla kaydedildi.|

## <a name="remarks"></a>Açıklamalar
 Her işlem veya iş parçacığına yalnızca bir ad atanabilir. Profil oluşturma öğesi adlandırıldıktan sonra, bu öğe için NameProfile öğesine yapılan sonraki çağrılar yok sayılır.

 Aynı ad farklı iş parçacıkları veya işlemlere verildiyse, rapor o düzeydeki tüm öğelerden bu adı taşıyan verileri içerecektir.

 Geçerli olandan farklı bir işlem veya iş parçacığı belirtirseniz, bunu yapmadan önce başlatılmış ve çalışır hale geldiğinden emin olmanız gerekir. Aksi takdirde, NameProfile yöntemi başarısız olur.

> [!IMPORTANT]
> CreateProcess () ve CreateThread () API işlevleri iş parçacığı veya işlem başlatılmadan önce dönebilir.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri

|Öğe|Değer|
|-|-|
|**Üst bilgi**|*VSPerf. h* dahil et|
|**Kitaplığı**|*VSPerf. lib* kullanın|
|**Unicode**|`NameProfileW`(Unicode) ve `NameProfileA` (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod, NameProfile işlev çağrısını gösterir. Örnek, kodun ANSI etkin işlevini çağırıp çağırmadığını öğrenmek için Win32 dize makroları ve ANSI için derleyici ayarları kullanımını varsayar.

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
- [Visual Studio profil oluşturucu apı başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
