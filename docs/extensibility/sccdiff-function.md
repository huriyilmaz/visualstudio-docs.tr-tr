---
description: Bu işlev, geçerli dosya (yerel diskte) ile kaynak denetim sisteminde son iade edildi sürümü arasındaki farkları görüntüler (veya isteğe bağlı olarak yalnızca denetler).
title: SccDiff İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1a644d677fb2a6f1d50909294649b270617a5bf0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117624"
---
# <a name="sccdiff-function"></a>SccDiff işlevi
Bu işlev, geçerli dosya (yerel diskte) ile kaynak denetim sisteminde son iade edildi sürümü arasındaki farkları görüntüler (veya isteğe bağlı olarak yalnızca denetler).

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 lpFileName

[in] Farkın istenen dosya adı.

 fOptions

[in] Komut bayrakları. Ayrıntılar için bkz. Açıklamalar.

 pvOptions

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini geri dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Çalışan kopya ve sunucu sürümü aynıdır.|
|SCC_I_FILESDIFFERS|Çalışan kopya, kaynak denetimi altındaki sürümden farklıdır.|
|SCC_I_RELOADFILE|Bir dosyanın veya projenin yeniden yüklenmiş olması gerekir.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişirken büyük olasılıkla ağ veya iletişim sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata; dosya farkı alınmdı.|
|SCC_E_FILENOTEXIST|Yerel dosya bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev iki farklı amaca hizmet verir. Varsayılan olarak, bir dosyada yapılan değişikliklerin listesini görüntüler. Kaynak denetimi eklentisi, kullanıcının diskte dosyası ile kaynak denetimi altındaki dosyanın en son sürümü arasındaki farkları görüntülemek için kendi penceresini seçer.

 Alternatif olarak, IDE'nin yalnızca bir dosyanın değişip değişmediğini belirlemesi gerekir. Örneğin, IDE'nin kullanıcıya bildirmeden bir dosyayı iade etmek için güvenli olup olmadığını belirlemesi gerekir. Bu durumda, IDE bayrağını `SCC_DIFF_CONTENTS` iletir. Kaynak denetimi eklentisi, kaynak denetimli dosyada diskte bulunan dosyayı bayta göre denetlemeli ve kullanıcıya hiçbir şey görüntülemeden iki dosyanın farklı olup olmadığını belirten bir değer iademalıdır.

 Performans iyileştirmesi olarak, kaynak denetim eklentisi tarafından çağrılan byte by-byte karşılaştırması yerine sağlamaları veya zaman damgasını temel alan bir alternatif kullanabilir: Bu karşılaştırma biçimleri açıkça daha hızlı ancak daha az `SCC_DIFF_CONTENTS` güvenilirdir. Tüm kaynak denetim sistemleri bu alternatif karşılaştırma yöntemlerini desteklemez ve eklentinin bir içerik karşılaştırması yapmak zorunda kalır. Tüm kaynak denetimi eklentilerinin en azından içerik karşılaştırması desteğine sahip olması gerekir.

> [!NOTE]
> Hızlı fark bayrakları birbirini dışlar. Bayrak geçmey için geçerlidir, ancak aynı anda birden fazla bayrak geçmek için geçerli değildir. `SCC_DIFF_QUICK_DIFF`Tüm bayrakları birleştiren bir maske olan , test etmek için kullanılabilir, ancak hiçbir zaman parametre olarak geçirilemez.

|`fOption`|Anlamı|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Büyük/harfe duyarsız karşılaştırma (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Boşluğu yoksayar (hızlı veya görsel fark için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Dosyayı sessizce, bayta göre karşılar.|
|SCC_DIFF_QD_CHECKSUM|Desteklene zaman sağlamaları aracılığıyla dosyayı sessiz bir şekilde karşılar. Desteklenmiyorsa, içeriği karşılaştırmaya geri döner.|
|SCC_DIFF_QD_TIME|Desteklendikleri zaman damgası aracılığıyla dosyayı sessiz bir şekilde karşılar. Desteklenmiyorsa, içeriği karşılaştırmaya geri döner.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
