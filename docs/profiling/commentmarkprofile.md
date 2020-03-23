---
title: Yorum İşareti Profili | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d45bab6b909fffa107158236d9050632f114c530
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772799"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
İşlev, `CommentMarkProfile` sayısal bir işaretçi ve metin dizesini . *vsp* dosyası. İşaret ve yorumun eklenmesi `CommentMarkProfile` için, işlevi içeren iş parçacığıiçin profil oluşturma nın ON olması gerekir.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametreler
 `lMarker`

 Eklemek için sayısal işaretçi. İşaretleyici 0'dan (sıfır) büyük veya eşit olmalıdır.

 `szComment`

 Eklemek için metin dizesini işaretçi. Dize NULL sonlandırıcı dahil olmak üzere 256 karakterden az olmalıdır.

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
 İşaret profili işlevini içeren iş parçacığının profil oluşturma durumu, VSInstr Mark komutu yla veya işlevlerle (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve yorumlar da üzerinde olmalıdır.

 Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığına eklenen bir profil işareti, veri kesiminin başlangıcını veya sonunu işaretlemek için kullanılabilir. *vsp* dosyası.

> [!IMPORTANT]
> CommentMarkProfile yöntemi sadece enstrümantasyon ile kullanılabilir.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Fonksiyon bilgileri

|||
|-|-|
|**Üst bilgi**|VSPerf.h ekle|
|**Kitaplığı**|VSPerf.lib kullanın|
|**Unicode**|(Unicode) ve `CommentMarkProfileW` `CommentMarkProfileA` (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod, CommentMarkProfile işlev çağrısını göstermektedir. Örnek, kodun işlev çağrısı nı çağırıp çağırmadığını belirlemek için Win32 dize makrolarının ve Unicode derleyici ayarlarının [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] kullanımını varsayar.

```cpp
void ExerciseCommentMarkProfile()
{
    // Declare and initalize variables to pass to
    // CommentMarkProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkProfile(
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio profilci API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
