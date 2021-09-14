---
description: Tam nitelikli dosya adlarının listesi verildiğinde, bu işlev bunları yerel sürücüye iade eder.
title: SccCheckout Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6168b2683f0201be2a4b140428b10fa9946bccf3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628880"
---
# <a name="scccheckout-function"></a>SccCheckout işlevi
Tam nitelikli dosya adlarının listesi verildiğinde, bu işlev bunları yerel sürücüye iade eder. Yorum, kullanıma alınan tüm dosyalar için geçerlidir. Açıklama bağımsız değişkeni bir dize olabilir `null` .

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 Nkarşıya

'ndaki Kullanıma almak için seçilen dosya sayısı.

 lpDosyaAdı

'ndaki Kullanıma alınan dosyaların tam nitelikli yerel yol adları dizisi.

 lpComment açıklaması

'ndaki Kullanıma alınan seçili dosyaların her birine uygulanacak yorum.

 fOptions

'ndaki Komut bayrakları (bkz. [belirli komutlar tarafından kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kullanıma alma başarılı oldu.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak kodu denetimi altında değil.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata. Dosya kullanıma alınamadı.|
|SCC_E_ALREADYCHECKEDOUT|Kullanıcının dosyası zaten kullanıma alındı.|
|SCC_E_FILEISLOCKED|Dosya kilitli ve yeni sürümlerin oluşturulmasını yasaklıyor.|
|SCC_E_FILEOUTEXCLUSIVE|Başka bir Kullanıcı bu dosyada özel kullanıma alma işlemi yapmış.|
|SCC_I_OPERATIONCANCELED|İşlem tamamlanmadan önce iptal edildi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Belirli komutlar tarafından kullanılan bitflags](../extensibility/bitflags-used-by-specific-commands.md)
