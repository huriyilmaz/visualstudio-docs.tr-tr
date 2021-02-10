---
title: SccDiff Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff2b2d5e5a0043cde17fecd2d59c084d2958e32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943120"
---
# <a name="sccdiff-function"></a>SccDiff işlevi
Bu işlev, geçerli dosya (yerel diskte) ve kaynak denetim sistemindeki son iade sürümü arasındaki farkları görüntüler (veya isteğe bağlı olarak denetler).

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpFileName

'ndaki Farkın istendiği dosya adı.

 fOptions

'ndaki Komut bayrakları. Ayrıntılar için bkz. açıklamalar.

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Çalışma kopyası ve sunucu sürümü aynıdır.|
|SCC_I_FILESDIFFERS|Çalışma kopyası, kaynak denetimi altındaki sürümden farklıdır.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata; dosya farkı alınamadı.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev iki farklı amaca hizmet eder. Varsayılan olarak, bir dosyadaki değişikliklerin listesini görüntüler. Kaynak denetimi eklentisi, kullanıcının diskteki dosyası ve kaynak denetimi altındaki dosyanın en son sürümü arasındaki farkları göstermek için kendi penceresini seçtiği herhangi bir biçimde açar.

 Alternatif olarak, IDE 'nin bir dosyanın değişip değişmediğini belirlemesi gerekebilir. Örneğin, IDE 'nin kullanıcıya bildirmeden bir dosyayı kullanıma almak için güvenli olup olmadığını belirlemesi gerekebilir. Bu durumda, IDE `SCC_DIFF_CONTENTS` bayrağa geçer. Kaynak denetimi eklentisinin, kaynak denetimli dosyada dosyayı disk üzerinde, bayt bayt olarak denetlemesi ve iki dosyanın kullanıcıya herhangi bir şey görüntülemeden farklı olup olmadığını gösteren bir değer döndürmesi gerekir.

 Bir performans iyileştirmesi olarak, kaynak denetimi eklentisi tarafından bir sağlama toplamı veya bir zaman damgasına göre, tarafından çağrılan bayt başına karşılaştırma yerine bir alternatif kullanabilir `SCC_DIFF_CONTENTS` : Bu karşılaştırma biçimleri daha hızlı ancak daha az güvenilir. Tüm kaynak denetim sistemleri bu alternatif karşılaştırma yöntemlerini desteklemeyebilir ve eklentinin bir içerik karşılaştırmasına geri dönmesi gerekebilir. Tüm kaynak denetimi eklentileri en azından bir içerik karşılaştırmayı desteklemelidir.

> [!NOTE]
> Hızlı fark bayrakları birbirini dışlıyor. Bayrak olmaması geçersizdir, ancak aynı anda birden fazla geçiş için geçerli değildir. `SCC_DIFF_QUICK_DIFF`tüm bayrakları birleştiren bir maske olan, test etmek için kullanılabilir, ancak asla bir parametre olarak geçirilmemelidir.

|`fOption`|Anlamı|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Büyük/küçük harfe duyarsız karşılaştırma (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Boşluğu yoksayar (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Dosya, bayt baytı ile sessizce karşılaştırır.|
|SCC_DIFF_QD_CHECKSUM|, Desteklenmiş olduğunda dosyayı sessizce bir sağlama toplamı ile karşılaştırır. Desteklenmiyorsa, içeriklerin karşılaştırmasına geri döner.|
|SCC_DIFF_QD_TIME|Destekleniyorsa, dosyayı zaman damgası aracılığıyla sessizce karşılaştırır. Desteklenmiyorsa, içeriklerin karşılaştırmasına geri döner.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
