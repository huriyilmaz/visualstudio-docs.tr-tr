---
title: SccHistory Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700657"
---
# <a name="scchistory-function"></a>SccHistory İşlevi
Bu işlev, belirtilen dosyaların geçmişini görüntüler.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parametreler
 `pvContext`

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 `hWnd`

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 `nFiles`

[içinde] `lpFileName` Dizide belirtilen dosya sayısı.

 `lpFileName`

[içinde] Dosyaların tam nitelikli adlarını diziliş.

 `fOptions`

[içinde] Komut bayrakları (şu anda kullanılmaz).

 `pvOptions`

[içinde] Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sürüm geçmişi başarıyla elde edildi.|
|SCC_I_RELOADFILE|Kaynak denetim sistemi, geçmişi (örneğin, eski bir sürümünü alarak) getirirken diskteki dosyayı gerçekten değiştirmiş, bu nedenle IDE bu dosyayı yeniden yüklemelidir.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_PROJNOTOPEN|Proje açılmadı.|
|SCC_E_NONSPECIFICERROR|Nonspesifik bir hata. Dosya geçmişi elde edilemedi.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, ana pencere olarak kullanarak `hWnd` her dosyanın geçmişini göstermek için kendi iletişim kutusunu görüntüleyebilir. Alternatif olarak, [sccOpenProject'e](../extensibility/sccopenproject-function.md) verilen isteğe bağlı metin çıktısı geri arama işlevi, desteklenirse kullanılabilir.

 Belirli koşullar altında, incelenen dosyanın bu aramanın yürütülmesi sırasında değişebileceğini unutmayın. Örneğin, geçmiş [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] komutu kullanıcıya dosyanın eski bir sürümünü alma şansı verir. Böyle bir durumda, kaynak denetim eklentisi Dosyayı yeniden yüklemesi gerektiği konusunda IDE'yi uyarmak için geri döner. `SCC_I_RELOAD`

> [!NOTE]
> Kaynak denetimi eklentisi bir dizi dosya için bu işlevi desteklemiyorsa, yalnızca ilk dosyanın dosya geçmişi görüntülenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
