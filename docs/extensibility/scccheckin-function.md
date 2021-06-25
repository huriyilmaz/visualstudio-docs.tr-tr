---
description: Bu işlev daha önce kullanıma alınmış dosyaları kaynak denetim sistemine denetler, değişiklikleri depolar ve yeni bir sürüm oluşturulur.
title: SccCheckin İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d324c03096df5178decd6f6954928df3f2c6b9aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904753"
---
# <a name="scccheckin-function"></a>SccCheckin işlevi
Bu işlev daha önce kullanıma alınmış dosyaları kaynak denetim sistemine denetler, değişiklikleri depolar ve yeni bir sürüm oluşturulur. Bu işlev, iade etmek için bir sayı ve bir dizi ad ile çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] SCC eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 nFiles

[in] Iade etmek için seçilen dosya sayısı.

 lpFileNames

[in] Denetlenecek dosyaların tam yerel yol adları dizisi.

 lpComment

[in] Denetlenen seçili dosyaların her biri için uygulanacak açıklama. Bu `NULL` parametre, kaynak denetimi eklentisinin bir açıklama sormalıdır.

 fOptions

[in] Komut bayrakları ( 0 veya `SCC_KEEP_CHECKEDOUT` ).

 pvOptions

[in] SCC eklentisine özgü seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Dosya başarıyla iade edildi.|
|SCC_E_FILENOTCONTROLLED|Seçilen dosya kaynak kodu denetimi altında değildir.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata. Dosya iade edildi.|
|SCC_E_NOTCHECKEDOUT|Kullanıcı dosyayı kullanıma alamadı, bu nedenle dosyayı iade amaz.|
|SCC_E_CHECKINCONFLICT|Aşağıdakiler nedeniyle iade gerçekleştiriledi:<br /><br /> - Başka bir kullanıcı daha önce giriş yaptı ve `bAutoReconcile` yanlıştı.<br /><br /> -veya-<br /><br /> - Otomatik birleştirme işlemi (örneğin dosyalar ikili olduğunda) olamaz.|
|SCC_E_VERIFYMERGE|Dosya otomatik olarak birleştirildi ama bekleyen kullanıcı doğrulamasında iade edildi.|
|SCC_E_FIXMERGE|Dosya otomatik olarak birleştirildi ancak el ile çözülmesi gereken birleştirme çakışması nedeniyle iade edildi.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Açıklama, iade ediliyor olan tüm dosyalar için geçerlidir. Açıklama bağımsız değişkeni bir dize olabilir; bu durumda kaynak denetimi eklentisi kullanıcıdan her dosya `null` için bir açıklama dizesi istendiğinde.

 Bağımsız değişkene, kullanıcının dosyayı iade etmek ve yeniden iade etmek için amacını `fOptions` `SCC_KEEP_CHECKEDOUT` belirtmek için bayrağının bir değeri verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
