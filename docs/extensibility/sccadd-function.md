---
description: Bu işlev, kaynak denetim sistemine yeni dosyalar ekler.
title: SccAdd İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cd73e3735478a89cb203aff8835f7535cecd0b7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158352"
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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 nFiles

[in] Dizide verilen şekilde geçerli projeye eklenecek dosya `lpFileNames` sayısı.

 lpFileNames

[in] Eklenecek dosyaların tam yerel adları dizisi.

 lpComment

[in] Eklenecek tüm dosyalara uygulanacak açıklama.

 pfOptions

[in] Dosya başına temelinde sağlanan komut bayrakları dizisi.

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Ekleme işlemi başarılı oldu.|
|SCC_E_FILEALREADYEXISTS|Seçilen dosya zaten kaynak denetimi altında.|
|SCC_E_TYPENOTSUPPORTED|Dosyanın türü (örneğin, ikili) kaynak denetim sistemi tarafından desteklenmiyor.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata; ekleme işlemi gerçekleştirilmadı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Burada her `fOptions` zamanki gibi, dosya başına bir seçenek `pfOptions` belirtimi olan `LONG` dizisiyle değiştirilir. Bunun nedeni, dosya türünün dosyadan dosyaya farklılık gösterebiliyor olabilir.

> [!NOTE]
> Aynı dosya için hem hem `SCC_FILETYPE_TEXT` de `SCC_FILETYPE_BINARY` seçeneklerini belirtmek geçersizdir, ancak ikisini de belirtmek için geçerlidir. hiçbiri ayarı ayarıyla aynı değildir; bu durumda kaynak denetimi eklentisi dosya türünü `SCC_FILETYPE_AUTO` otomatik olarak algılamaz.

 Dizide kullanılan bayrakların listesi aşağıda `pfOptions` verilmiştir:

|Seçenek|Değer|Anlamı|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|Kaynak denetimi eklentisi, dosya türünü algılamalı.|
|SCC_FILETYPE_TEXT|0x01|BIR ASCII metin dosyasını gösterir.|
|SCC_FILETYPE_BINARY|0x02|ASCII metni dışında bir dosya türünü gösterir.|
|SCC_ADD_STORELATEST|0x04|Dosyanın yalnızca en son kopyasını depolar, deltaları depolar.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Dosyayı ANSI metni olarak davranır.|
|SCC_FILETYPE_UTF8|0x10|Dosyayı UTF8 biçiminde Unicode metin olarak davranır.|
|SCC_FILETYPE_UTF16LE|0x20|Dosyayı UTF16 Little Endian biçiminde Unicode metin olarak davranır.|
|SCC_FILETYPE_UTF16BE|0x40|Dosyayı UTF16 Big Endian biçiminde Unicode metin olarak davranır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
