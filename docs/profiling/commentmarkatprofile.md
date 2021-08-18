---
title: CommentMarkAtProfile | Microsoft Docs
description: . Vsp dosyasına bir zaman damgası değeri, sayısal bir işaret ve açıklama dizesi eklemek için CommentMarkAtProfile yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 59cdbe8bd3be23c2f356cb171449806cea5def87
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107907"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
`CommentMarkAtProfile`Yöntemi bir zaman damgası değeri, sayısal bir işaret ve *. vsp* dosyasına bir açıklama dizesi ekler. Zaman damgası değeri, dış olayları senkronize etmek için kullanılabilir. İşaret ve Açıklama eklenecek şekilde, CommentMarkAtProfile işlevini içeren iş parçacığının profil oluşturma açık olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Parametreler
 `dnTimestamp`

 Bir zaman damgası değerini temsil eden 64 bitlik bir tamsayı.

 `lMarker`

 Eklenecek sayısal işaret. İşaretleyici 0 (sıfır) değerinden büyük veya buna eşit olmalıdır.

 `szComment`

 Eklenecek metin dizesine yönelik bir işaretçi. Dize, NULL Sonlandırıcı dahil 256 karakterden az olmalıdır.

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri
 İşlev, **PROFILE_COMMAND_STATUS** numaralandırma kullanılarak başarılı veya başarısız olduğunu gösterir. Dönüş değeri aşağıdakilerden biri olabilir:

|Sının|Açıklama|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Parametre 0 ' dan küçük veya buna eşit. Bu değerler ayrılmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_NEVER|Profil oluşturma modu, işlev çağrıldığında hiçbir zaman olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_MODE_OFF|İşlev çağrıldığında profil oluşturma modu OFF olarak ayarlanmıştır. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_NO_SUPPORT|Bu bağlamda işaret desteği yok. İşaret ve açıklama kaydedilmez.|
|MARK_ERROR_OUTOFMEMORY|Olayı kaydetmek için bellek yoktu. İşaret ve açıklama kaydedilmez.|
|MARK_TEXTTOOLONG|Dize en fazla 256 karakter sınırını aşıyor. Açıklama dizesi kesilir ve işaret ve açıklama kaydedilir.|
|MARK_OK|Başarıyı göstermek için MARK_OK döndürülür.|

## <a name="remarks"></a>Açıklamalar
 Mark komutuyla veya API işlevleriyle (CommentMarkAtProfile, CommentMarkProfile veya MarkProfile) eklenen işaretler ve açıklamalar olduğunda, işaret profili işlevini içeren iş parçacığının profil oluşturma durumu açık olmalıdır. Profil işaretleri kapsamda geneldir. Örneğin, bir iş parçacığına yerleştirilmiş bir profil işareti,. vsp dosyasındaki herhangi bir iş parçacığında bir veri segmentinin başlangıcını veya sonunu işaretlemek için kullanılabilir.

> [!IMPORTANT]
> CommentMarkAtProfile yöntemlerinin yalnızca izleme ile kullanılması gerekir.

## <a name="net-framework-equivalent"></a>.NET Framework eşdeğeri
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>İşlev bilgileri

|Öğe|Değer|
|-|-|
|**Üst bilgi**|*VSPerf. h* dahil et|
|**Kitaplığı**|*VSPerf. lib* kullanın|
|**Unicode**|CommentMarkAtProfileW (Unicode) ve CommentMarkAtProfileA (ANSI) olarak uygulanır.|

## <a name="example"></a>Örnek
 Aşağıdaki kod, CommentMarkAtProfile genel işlev çağrısının kullanımını gösterir. Örnek, kodun ANSI etkin işlevini çağırıp çağırmadığını öğrenmek için Win32 dize makroları ve ANSI için derleyici ayarları kullanımını varsayar.

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
- [Visual Studio Profil oluşturucu API başvurusu (yerel)](../profiling/visual-studio-profiler-api-reference-native.md)
