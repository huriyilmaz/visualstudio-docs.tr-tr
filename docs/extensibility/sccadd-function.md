---
title: SccAdd Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701308"
---
# <a name="sccadd-function"></a>SccAdd fonksiyonu
Bu işlev kaynak denetim sistemine yeni dosyalar ekler.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] `lpFileNames` Dizide verilen geçerli projeye eklenecek seçili dosya sayısı.

 lpFileNames

[içinde] Eklenecek dosyaların tam nitelikli yerel adlarını dizi.

 lpYorum yap

[içinde] Eklenecek tüm dosyalara uygulanacak açıklama.

 pfOptions

[içinde] Dosya başına sağlanan komut bayrakları dizisi.

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Ekleme işlemi başarılı oldu.|
|SCC_E_FILEALREADYEXISTS|Seçili dosya zaten kaynak denetimi altında.|
|SCC_E_TYPENOTSUPPORTED|Dosyanın türü (örneğin, ikili) kaynak denetim sistemi tarafından desteklenmez.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Nonspesifik başarısızlık; gerçekleştirilmeyen ekleyin.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Her `fOptions` zamanki dosya başına bir `pfOptions` `LONG` seçenek belirtimi ile, bir dizi ile burada değiştirilir. Bunun nedeni, dosya türünün dosyadan dosyaya farklılık gösterebileceğidir.

> [!NOTE]
> Aynı dosya için hem `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` de seçenekleri belirtmek geçersizdir, ancak ikisini de belirtmek için geçerlidir. Ne ayarı ayarla `SCC_FILETYPE_AUTO`aynıdır , bu durumda kaynak denetim eklentisi dosya türünü otomatik algılar.

 Aşağıda dizide kullanılan bayrakların `pfOptions` listesi verilmiştir:

|Seçenek|Değer|Anlamı|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Kaynak denetim eklentisi dosya türünü algılamalıdır.|
|SCC_FILETYPE_TEXT|0x01|ASCII metin dosyalarını gösterir.|
|SCC_FILETYPE_BINARY|0x02|ASCII metni dışında bir dosya türünü gösterir.|
|SCC_ADD_STORELATEST|0x04|Dosyanın sadece en son kopyasını saklar, delta yok.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Dosyayı ANSI metni olarak ele verir.|
|SCC_FILETYPE_UTF8|0x10|Dosyayı UTF8 biçiminde Unicode metni olarak ele verir.|
|SCC_FILETYPE_UTF16LE|0x20|Dosyayı UTF16 Little Endian formatında Unicode metni olarak ele verir.|
|SCC_FILETYPE_UTF16BE|0x40|Dosyayı UTF16 Big Endian formatında Unicode metni olarak ele verir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
