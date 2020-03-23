---
title: Yorum İşaretleriProfili | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 51028dce1d60c0d01c83cee509a1ed7321855437
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777848"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
Yöntem, `CommentMarkAtProfile` bir zaman damgası değeri, sayısal işaret ve bir açıklama dizesi ekler. *vsp* dosyası. Zaman damgası değeri dış olayları eşitlemek için kullanılabilir. İşaret ve yorumun eklenmesi için, CommentMarkAtProfile işlevini içeren iş parçacığının profil oluşturma özelliği ON olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametreler
 `dnTimestamp`

 Zaman damgası değerini temsil eden 64 bit'lik tamsayı.

 `lMarker`

 Eklenecek sayısal işaretçi. İşaretleyici 0'dan (sıfır) büyük veya eşit olmalıdır.

 `szComment`

 Eklemek için metin dizesine bir işaretçi. Dize NULL sonlandırıcı dahil olmak üzere 256 karakterden az olmalıdır.

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
 İşaret profili işlevini içeren iş parçacığının profil oluşturma durumu, İşaretle komutuyla veya API işlevlerine (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve yorumlar da üzerinde olmalıdır. Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığına eklenen bir profil işareti, .vsp dosyasındaki herhangi bir iş parçacığındaki bir veri kesiminin başlangıcını veya sonunu işaretlemek için kullanılabilir.

> [!IMPORTANT]
> CommentMarkAtProfile yöntemleri sadece enstrümantasyon ile kullanılmalıdır.

## <a name="net-framework-equivalent"></a>.NET Çerçeve eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Fonksiyon bilgileri

|||
|-|-|
|**Üst bilgi**|*VSPerf.h* ekle|
|**Kitaplığı**|*VSPerf.lib* kullanın|
|**Unicode**|CommentMarkAtProfileW (Unicode) ve CommentMarkAtProfileA (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod, CommentMarkAtProfile genel işlev çağrısının kullanımını göstermektedir. Örnek, kodun ANSI etkin işlevini çağırıp çağırmadığını belirlemek için Win32 dize makrolarının ve ANSI için derleyici ayarlarının kullanımını varsayar.

```cpp
void ExerciseCommentMarkAtProfile(void)
{
    // Declare and initalize variables to pass to
    // CommentMarkAtProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    int64 timeStamp = 0x1111;
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkAtProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkAtProfile(
        timeStamp,
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
    pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Profiler API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
