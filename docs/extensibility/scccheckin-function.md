---
title: SccCheckin Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701179"
---
# <a name="scccheckin-function"></a>SccCheckin fonksiyonu
Bu işlev, daha önce kullanıma alınan dosyaları kaynak denetim sistemine denetler, değişiklikleri depolar ve yeni bir sürüm oluşturur. Bu işlev, bir sayım ve iade edilecek dosyaların adlarını bir dizi ile çağrılır.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] SCC eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] İade edilecek dosya sayısı.

 lpFileNames

[içinde] İade edilecek dosyaların tam nitelikli yerel yol adlarını dizilimi.

 lpYorum yap

[içinde] İade edilen seçili dosyaların her birine uygulanacak açıklama. Bu parametre, kaynak denetim eklentisinin bir yorum için istekte olması durumunda. `NULL`

 fSeçenekler

[içinde] Komut bayrakları, 0 `SCC_KEEP_CHECKEDOUT`veya.

 pvOptions

[içinde] SCC eklentisi özel seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Dosya başarıyla iade edildi.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değildir.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata. Dosya iade edilmedi.|
|SCC_E_NOTCHECKEDOUT|Kullanıcı dosyayı kullanıma açmadığı için iade edemez.|
|SCC_E_CHECKINCONFLICT|İade işlemi yapılamadığı için:<br /><br /> - Başka bir kullanıcı önceden `bAutoReconcile` giriş yaptı ve yanlış oldu.<br /><br /> -veya-<br /><br /> - Otomatik birleştirme yapılamaz (örneğin, dosyalar ikili olduğunda).|
|SCC_E_VERIFYMERGE|Dosya otomatik olarak birleştirilmiştir, ancak bekleyen kullanıcı doğrulamasında iade edilmemiştir.|
|SCC_E_FIXMERGE|Dosya otomatik olarak birleştirilmiştir, ancak el ile çözülmesi gereken bir birleştirme çakışması nedeniyle iade edilmemiştir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Açıklama, iade edilen tüm dosyalar için geçerlidir. Açıklama bağımsız değişkeni, kaynak denetimi eklentisinin kullanıcıdan her dosya için bir yorum dizesini isteyebilir olduğu bir `null` dize olabilir.

 Bağımsız `fOptions` değişkene, kullanıcının `SCC_KEEP_CHECKEDOUT` dosyayı iade etme ve yeniden kullanıma açma niyetini belirtmek için bayrağın değeri verilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
