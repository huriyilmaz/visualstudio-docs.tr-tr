---
description: Bu işlev belirtilen dosyaların geçmişini görüntüler.
title: SccHistory İşlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902546"
---
# <a name="scchistory-function"></a>SccHistory İşlevi
Bu işlev belirtilen dosyaların geçmişini görüntüler.

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

[in] Kaynak denetimi eklentisi bağlam yapısı.

 `hWnd`

[in] Kaynak denetimi eklentisinin sağladığı iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi tanıtıcısı.

 `nFiles`

[in] Dizide belirtilen dosya `lpFileName` sayısı.

 `lpFileName`

[in] Dosyaların tam adları dizisi.

 `fOptions`

[in] Komut bayrakları (şu anda kullanılmadı).

 `pvOptions`

[in] Kaynak denetimi eklentisine özgü seçenekler.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Sürüm geçmişi başarıyla elde edildi.|
|SCC_I_RELOADFILE|Kaynak denetim sistemi, geçmişi getirirken (örneğin, eski bir sürümünü alınarak) diskte dosyayı değiştirerek IDE'nin bu dosyayı yeniden yüklemesi gerekir.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_OPNOTSUPPORTED|Kaynak denetim sistemi bu işlemi desteklemez.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya sorun sorun nedeniyle kaynak denetim sistemine erişilirken bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_PROJNOTOPEN|Proje açık değil.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen hata. Dosya geçmişi alınamıyor.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi eklentisi, üst pencere olarak kullanarak her dosyanın geçmişini göstermek için kendi iletişim `hWnd` kutusunu gösterebilir. Alternatif olarak, desteklense [SccOpenProject'e](../extensibility/sccopenproject-function.md) sağlanan isteğe bağlı metin çıkışı geri çağırma işlevi kullanılabilir.

 Belirli koşullar altında, incelenecek dosyanın bu çağrının yürütülmesi sırasında değişebilirsiniz. Örneğin, [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] geçmiş komutu kullanıcıya dosyanın eski bir sürümünü elde etme şansı verir. Böyle bir durumda kaynak denetimi eklentisi, IDE'nin dosyayı yeniden `SCC_I_RELOAD` yüklemesi gerektiğini uyarmak için geri döner.

> [!NOTE]
> Kaynak denetimi eklentisi bir dosya dizisi için bu işlevi desteklemezse yalnızca ilk dosyanın dosya geçmişi görüntülenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
