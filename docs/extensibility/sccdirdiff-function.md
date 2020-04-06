---
title: SccDirDiff Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701008"
---
# <a name="sccdirdiff-function"></a>SccDirDiff fonksiyonu
Bu işlev, istemci diskindeki geçerli yerel dizini ile kaynak denetimi altında ilgili proje arasındaki farkları görüntüler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpDirName

[içinde] Görsel bir fark göstermek için yerel dizine tam nitelikli yol.

 Dwflags

[içinde] Komut bayrakları (bkz. Açıklamalar bölümü).

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Diskteki dizin, kaynak kodu denetimindeki projeyle aynıdır.|
|SCC_I_FILESDIFFER|Diskteki dizin, kaynak kodu denetimindeki projeden farklıdır.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|
|SCC_E_FILENOTCONTROLLED|Dizin kaynak kodu denetimi altında değildir.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|
|SCC_E_FILENOTEXIST|Yerel dizin bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetim eklentisinin kullanıcıya belirli bir dizindeki değişikliklerin listesini görüntülemesini sağlamak için kullanılır. Eklenti, kullanıcının diskteki dizini ile ilgili proje arasındaki farkları sürüm denetimi altında görüntülemek için kendi seçtiği bir biçimde kendi penceresini açar.

 Bir eklenti dizinlerin karşılaştırılmalarını destekliyorsa, "hızlı dağıt" seçenekleri desteklenmese bile dizinlerin dosya adı bazında karşılaştırılmayı desteklemesi gerekir.

|`dwFlags`|Yorum|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Büyük/küçük harf duyarlı karşılaştırması (hızlı diff veya görsel için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Beyaz alanı yok sayar (hızlı-diff veya görsel için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Kaynak denetim eklentisi tarafından desteklenirse, dizin, byte by byte sessizce karşılaştırır.|
|SCC_DIFF_QD_CHECKSUM|Eklenti tarafından desteklenirse, bir çekum aracılığıyla dizinsessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CONTENTS geri düşer.|
|SCC_DIFF_QD_TIME|Eklenti tarafından desteklenirse, dizin zaman damgası üzerinden sessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CHECKSUM veya SCC_DIFF_QD_CONTENTS geri düşer.|

> [!NOTE]
> Bu [işlev, SccDiff](../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Ancak, bir kaynak denetim eklentisi dizinler için "hızlı dağıt" işlemini desteklememeyi seçebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
