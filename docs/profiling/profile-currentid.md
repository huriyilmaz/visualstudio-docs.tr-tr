---
title: PROFILE_CURRENTID | Microsoft Docs
description: İşlevin, özel olarak belirtilen bir iş parçacığı veya işlem üzerinde çalışmasını sağlamak için PROFILE_CURRENTID nasıl kullanılacağını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5171753ff8ea6722cf1d97e155352e3899fb5562
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719493"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID, NameProfile, StartProfile, StopProfile, SuspendProfile ve ResumeProfile işlevlerine yapılan çağrıda iş parçacığı KIMLIĞI veya işlem KIMLIĞI için sözde belirteci döndürür. İşlevin, özel olarak belirtilen bir iş parçacığı veya işlem üzerinde çalışmasını sağlamak için bunu kullanın.

## <a name="example-1"></a>Örnek 1
 PROFILE_CURRENTID, *VSPerf. h* içinde şu şekilde tanımlanır:

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>Örnek 2
 Aşağıdaki örnekte PROFILE_CURRENTID gösterilmektedir. Örnek, [StartProfile](../profiling/startprofile.md) işlevine yapılan çağrıda geçerli iş parçacığını tanımlayan bir parametre olarak PROFILE_CURRENTID kullanır.

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
- [Visual Studio profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
