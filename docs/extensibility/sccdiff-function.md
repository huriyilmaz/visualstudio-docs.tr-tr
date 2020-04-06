---
title: SccDiff Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701031"
---
# <a name="sccdiff-function"></a>SccDiff fonksiyonu
Bu işlev, geçerli dosya (yerel diskte) ile kaynak denetim sistemindeki son iade edilmiş sürümü arasındaki farkları görüntüler (veya isteğe bağlı olarak yalnızca denetler).

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametreler
 pvContext

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpFileName

[içinde] Farkın istendiği dosya adı.

 fSeçenekler

[içinde] Komut bayrakları. Ayrıntılar için Açıklamalar'a bakın.

 pvOptions

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Çalışan kopya ve sunucu sürümü aynıdır.|
|SCC_I_FILESDIFFERS|Çalışan kopya, kaynak denetimi altındaki sürümden farklıdır.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmesi gerekir.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Nonspesifik başarısızlık; dosya farkı elde edilemedi.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev iki farklı amac için hizmet eder. Varsayılan olarak, bir dosyada yapılan değişikliklerin listesini görüntüler. Kaynak denetimi eklentisi, kullanıcının dosyası yla dosyanın en son sürümü arasındaki farkları kaynak denetimi altında görüntülemek için kendi penceresini, hangi biçimde seçerse seçsin, açar.

 Alternatif olarak, IDE'nin yalnızca bir dosyanın değişip değişmediğini belirlemesi gerekebilir. Örneğin, IDE kullanıcıya bildirmeden bir dosyayı kullanıma almak için güvenli olup olmadığını belirlemek gerekebilir. Bu durumda, IDE bayrak `SCC_DIFF_CONTENTS` geçer. Kaynak denetimi eklentisi, dosyayı diskteki bayt byby byte, kaynak denetimli dosyaya karşı denetlemeli ve kullanıcıya hiçbir şey göstermeden iki dosyanın farklı olup olmadığını gösteren bir değer döndürmelidir.

 Performans optimizasyonu olarak, kaynak kontrol eklentisi tarafından `SCC_DIFF_CONTENTS`çağrılan bayt-byte karşılaştırma yerine bir çekum veya zaman damgası dayalı bir alternatif kullanabilirsiniz: karşılaştırma bu formları açıkça daha hızlı ama daha az güvenilir. Tüm kaynak denetim sistemleri bu alternatif karşılaştırma yöntemlerini desteklemeyebilir ve eklentinin bir içerik karşılaştırmasına geri dönmesi gerekebilir. Tüm kaynak denetimi eklentileri en azından bir içerik karşılaştırması desteklemelidir.

> [!NOTE]
> Hızlı fark bayrakları birbirini dışlar. Bayrak geçmemek geçerlidir, ancak aynı anda birden fazla bayrak geçmek için geçerli değildir. `SCC_DIFF_QUICK_DIFF`, tüm bayrakları birleştiren bir maske, test etmek için kullanılabilir, ancak bir parametre olarak geçirilmemelidir.

|`fOption`|Anlamı|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Büyük/küçük harf duyarlı karşılaştırması (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Beyaz alanı yok sayar (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Sessizce dosya, bybayt karşılaştırır.|
|SCC_DIFF_QD_CHECKSUM|Desteklendiğinde dosyayı bir çekum aracılığıyla sessizce karşılaştırır. Desteklenmezse, içeriğin karşılaştırılmasına geri döner.|
|SCC_DIFF_QD_TIME|Desteklendiğinde dosyayı zaman damgası üzerinden sessizce karşılaştırır. Desteklenmezse, içeriğin karşılaştırılmasına geri döner.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
