---
title: SccCheckout Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701102"
---
# <a name="scccheckout-function"></a>SccCheckout fonksiyonu
Tam nitelikli dosya adlarının bir listesi verilirse, bu işlev bunları yerel sürücüye denetler. Açıklama, kullanıma alınan tüm dosyalar için geçerlidir. Açıklama bağımsız değişkeni `null` bir dize olabilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 nDosyalar

[içinde] Kullanıma alınacak dosya sayısı.

 lpFileNames

[içinde] Kullanıma alınacak dosyaların tam nitelikli yerel yol adlarını dizilimi.

 lpYorum yap

[içinde] Kullanıma alınan seçili dosyaların her birine uygulanacak açıklama.

 fSeçenekler

[içinde] Komut bayrakları [(bkz. belirli komutlar tarafından kullanılan Bit bayrakları).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Çıkış başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değildir.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata. Dosya kullanıma alınmadı.|
|SCC_E_ALREADYCHECKEDOUT|Kullanıcı dosyayı kullanıma almıştır.|
|SCC_E_FILEISLOCKED|Dosya kilitli, yeni sürümlerin oluşturulmasını yasaklayan.|
|SCC_E_FILEOUTEXCLUSIVE|Başka bir kullanıcı bu dosya üzerinde özel bir ödeme yaptı.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan iptal edildi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [Belirli komutlar tarafından kullanılan Bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md)
