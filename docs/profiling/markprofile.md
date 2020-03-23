---
title: İşaretProfili | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f53b51f9e78e2cb5d327abd3a79ebf2faa3a9204
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778576"
---
# <a name="markprofile"></a>MarkProfile
Yöntem, `MarkProfile` ''ye bir profil işareti ekler. *vsp* dosyası. `MarkProfile` İşaretin takılması için işlevi içeren iş parçacığının profil oluşturma özelliği ON olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Parametreler
 `lMarker`

 Eklenecek işaretçi. İşaretçi 0'dan (sıfır) büyük veya eşit olmalıdır.

## <a name="property-valuereturn-value"></a>Özellik değeri/iade değeri
 İşlev, **numaralandırma PROFILE_COMMAND_STATUS** kullanarak başarı veya başarısızlığı gösterir. İade değeri aşağıdakilerden biri olabilir:

|Numaralayıcı|Açıklama|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametre 0'dan küçük veya eşittir. Bu değerler ayrılmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında NEVER olarak ayarlandı. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_OFF|Profil oluşturma modu, işlev çağrıldığında KAPALI olarak ayarlandı. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işaret desteği yok. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek kullanılamadı. İşaret ve açıklama kaydedilmez.|
|MARK_TEXTTOOLONG|Dize en fazla 256 karakteri aşıyor. Açıklama dizesi kesilir ve işaret ve açıklama kaydedilir.|
|MARK_OK|MARK_OK başarıyı göstermek için döndürülür.|

## <a name="remarks"></a>Açıklamalar
 İşaret değeri. *MarkProfile* işlevini içeren iş parçacığı profilleniyorsa, kod her çalıştığında vsp dosyası. MarkProfile'ı birden çok kez arayabilirsiniz.

 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığına eklenen bir profil işareti, veri kesiminin başlangıcını veya sonunu işaretlemek için kullanılabilir. *vsp* dosyası.

 İşaret profili işlevini içeren iş parçacığının profil oluşturma durumu, İşaretle komutuyla veya API işlevlerine (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve yorumlar da üzerinde olmalıdır.

> [!IMPORTANT]
> MarkProfile yöntemi yalnızca enstrümantasyon profilleme ile kullanılmalıdır.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Fonksiyon bilgileri
 Üstbilgi: *VSPerf.h'de* beyan edile

 İthalat kitaplığı: *VSPerf.lib*

## <a name="example"></a>Örnek
 Aşağıdaki kod MarkProfile işlevini göstermektedir.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
