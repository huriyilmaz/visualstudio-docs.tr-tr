---
description: Bu işlev, kaynak denetim sistemine yeni dosyalar ekler.
title: SccAdd Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f654429f8c3faefe05a6410a3c732a6a4b1d083b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221736"
---
# <a name="sccadd-function"></a>SccAdd işlevi
Bu işlev, kaynak denetim sistemine yeni dosyalar ekler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 Nkarşıya

'ndaki Geçerli projeye dizide verilen şekilde eklenmek üzere seçilen dosya sayısı `lpFileNames` .

 lpDosyaAdı

'ndaki Eklenecek dosyaların tam nitelikli yerel adları dizisi.

 lpComment açıklaması

'ndaki Eklenmekte olan tüm dosyalara uygulanacak yorum.

 Pfseçenekleri

'ndaki Dosya başına temelinde sunulan komut bayrakları dizisi.

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Ekleme işlemi başarılı oldu.|
|SCC_E_FILEALREADYEXISTS|Seçili dosya zaten kaynak denetimi altında.|
|SCC_E_TYPENOTSUPPORTED|Dosya türü (örneğin, ikili) kaynak denetim sistemi tarafından desteklenmiyor.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata; ekleme gerçekleştirilmedi.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Her zamanki gibi, her `fOptions` `pfOptions` dosya için tek bir seçenek belirtimine sahip bir dizi tarafından burada yer alır `LONG` . Bunun nedeni dosya türünün dosyadan dosyaya değişebiliyor olması olabilir.

> [!NOTE]
> Aynı dosya için hem hem de `SCC_FILETYPE_TEXT` seçeneklerini belirtmek geçersizdir `SCC_FILETYPE_BINARY` , ancak bunu belirtmek geçerli değildir. Ayarın hiçbiri, ayarıyla aynı değildir `SCC_FILETYPE_AUTO` , bu durumda kaynak denetimi eklentisi dosya türünü oto algılar.

 Dizide kullanılan bayrakların listesi aşağıda verilmiştir `pfOptions` :

|Seçenek|Değer|Anlamı|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|-|Kaynak denetimi eklentisi dosya türünü algılamamalıdır.|
|SCC_FILETYPE_TEXT|0x01|ASCII metin dosyasını gösterir.|
|SCC_FILETYPE_BINARY|0x02|ASCII metni dışında bir dosya türünü gösterir.|
|SCC_ADD_STORELATEST|0x04|Yalnızca dosyanın en son kopyasını depolar, hiçbir deltas yoktur.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Dosyayı ANSI metni olarak değerlendirir.|
|SCC_FILETYPE_UTF8|0x10|Dosyayı UTF8 biçiminde Unicode metin olarak değerlendirir.|
|SCC_FILETYPE_UTF16LE|0x20|Dosyayı UTF16 little endian biçiminde Unicode metin olarak değerlendirir.|
|SCC_FILETYPE_UTF16BE|0x40|Dosyayı UTF16 Big endian biçiminde Unicode metin olarak değerlendirir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
