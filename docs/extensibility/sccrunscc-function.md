---
description: Bu işlev, kaynak denetimi yönetim aracını çağırır.
title: SccRunScc Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e78e58eafebd06d1ce7c710a31ce295b49f26340
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073826"
---
# <a name="sccrunscc-function"></a>SccRunScc İşlevi
Bu işlev, kaynak denetimi yönetim aracını çağırır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 Nkarşıya

'ndaki Dizide belirtilen dosya sayısı `lpFileNames` .

 lpDosyaAdı

'ndaki Seçili dosya adlarından oluşan dizi.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Kaynak denetimi yönetim aracı başarıyla çağrıldı.|
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|
|SCC_E_INITIALIZEFAILED|Kaynak denetim sistemi başlatılamadı.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|
|SCC_E_CONNECTIONFAILURE|Kaynak denetim sistemine bağlanılamadı.|
|SCC_E_FILENOTCONTROLLED|Seçili dosya kaynak denetimi altında değil.|
|SCC_E_NONSPECIFICERROR|Özel olmayan hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, çağıranın bir dış yönetim aracı aracılığıyla kaynak denetim sisteminin tüm özelliklerine erişmesine olanak tanır. Kaynak denetim sisteminde kullanıcı arabirimi yoksa, kaynak denetimi eklentisi gerekli yönetim işlevlerini gerçekleştirmek için bir arabirim uygulayabilir.

 Bu işlev, şu anda seçili dosyalar için bir sayı ve dosya adı dizisiyle çağrılır. Yönetim Aracı destekliyorsa, dosya listesi yönetim arabirimindeki dosyaları önceden seçmek için kullanılabilir; Aksi takdirde, liste yok sayılabilir.

 Bu işlev genellikle Kullanıcı **Dosya** **\<Source Control Server>**  ->  **kaynağı denetim** menüsünden başlatmayı seçtiğinde çağrılır. Bu **başlatma** menü seçeneği, bir kayıt defteri girişi ayarlanarak her zaman devre dışı bırakılabilir veya gizlenebilir. Ayrıntılar için bkz. [nasıl yapılır: kaynak denetim eklentisi yüklemesi](../extensibility/internals/how-to-install-a-source-control-plug-in.md) . Bu işlev yalnızca, [SccInitialize](../extensibility/sccinitialize-function.md) yetenek bitini döndürürse çağrılır `SCC_CAP_RUNSCC` (Bu ve diğer yetenek bitleri hakkındaki ayrıntılar Için bkz. [yetenek bayrakları](../extensibility/capability-flags.md) ).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [Nasıl Yapılır: Kaynak Denetimi Eklentisi Yükleme](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Özellik Bayrakları](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
