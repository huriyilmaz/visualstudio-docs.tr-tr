---
title: PROFILE_CURRENTID | Microsoft Docs
description: İşlevin özellikle PROFILE_CURRENTID iş parçacığında veya işlemde çalışmasına neden olmak için bu işlevin nasıl kullanılamayacaklarını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0cb855db8f233a35567188c5f44f7e9a3d972de7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060849"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
Bu PROFILE_CURRENTID NameProfile, StartProfile, StopProfile, SuspendProfile ve ResumeProfile işlevlerine yapılan bir çağrıda iş parçacığı kimliği veya işlem kimliği için sahte belirteci döndürür. İşlevin, özellikle belirtilen bir iş parçacığı yerine geçerli iş parçacığında veya işlemde çalışmasına neden olmak için bunu kullanın.

## <a name="example-1"></a>Örnek 1
 PROFILE_CURRENTID *VSPerf.h içinde şu şekilde* tanımlanır:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>Örnek 2
 Aşağıdaki örnekte, aşağıdaki PROFILE_CURRENTID. Örnek, PROFILE_CURRENTID [startProfile](../profiling/startprofile.md) işlevine yapılan bir çağrıda geçerli iş parçacığını tanımlayan bir parametre olarak kullanır.

```cpp
void ExerciseProfileCurrentID()
{
    // Declare ProfileOperationResult enumeration
    // to hold return value of a call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    profileResult = StartProfile(
        PROFILE_GLOBALLEVEL,
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
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
