---
description: Bu işlev, istemci diskinde geçerli yerel dizin ve kaynak denetimi altındaki karşılık gelen proje arasındaki farkları görüntüler.
title: SccDirDiff Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 15f4cd3bd1175cbea11656f62159a56f1c57bb98
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158326"
---
# <a name="sccdirdiff-function"></a>SccDirDiff işlevi
Bu işlev, istemci diskinde geçerli yerel dizin ve kaynak denetimi altındaki karşılık gelen proje arasındaki farkları görüntüler.

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
 pContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpDirName

'ndaki Görsel bir farkı göstermek için yerel dizinin tam yolu.

 dwFlags

'ndaki Komut bayrakları (bkz. açıklamalar bölümü).

 pvOptions

'ndaki Kaynak denetimi eklentisi özel seçenekleri.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Disk üzerindeki dizin, kaynak kodu denetimindeki projeyle aynıdır.|
|SCC_I_FILESDIFFER|Disk üzerindeki dizin, kaynak kodu denetimindeki projeden farklı.|
|SCC_I_RELOADFILE|Bir dosya veya projenin yeniden yüklenmesi gerekiyor.|
|SCC_E_FILENOTCONTROLLED|Dizin, kaynak kodu denetimi altında değil.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmiyor.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|
|SCC_E_FILENOTEXIST|Yerel dizin bulunamadı.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetimi eklentisinin kullanıcıya belirtilen bir dizin üzerinde yapılan değişikliklerin bir listesini görüntülemesini istemek için kullanılır. Eklenti, kullanıcının disk üzerindeki dizini ile sürüm denetimi altında karşılık gelen proje arasındaki farkları göstermek için kendi penceresini kendi tercih ettiği biçimde açar.

 Bir eklenti dizinlerin karşılaştırılmasını destekliyorsa, "hızlı fark" seçenekleri desteklenmediği halde bir dosya adı temelinde dizinlerin karşılaştırılmasını desteklememelidir.

|`dwFlags`|Yorum|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Büyük/küçük harfe duyarsız karşılaştırma (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_IGNORESPACE|Boşluğu yoksayar (hızlı fark veya görsel için kullanılabilir).|
|SCC_DIFF_QD_CONTENTS|Kaynak denetimi eklentisi tarafından destekleniyorsa, dizini, bayt bayt olarak sessizce karşılaştırır.|
|SCC_DIFF_QD_CHECKSUM|Eklenti tarafından destekleniyorsa, dizini bir sağlama toplamı aracılığıyla sessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CONTENTS geri döner.|
|SCC_DIFF_QD_TIME|Eklenti tarafından destekleniyorsa, dizini zaman damgası aracılığıyla sessizce karşılaştırır veya desteklenmiyorsa SCC_DIFF_QD_CHECKSUM veya SCC_DIFF_QD_CONTENTS geri döner.|

> [!NOTE]
> Bu işlev, [SccDiff](../extensibility/sccdiff-function.md)ile aynı komut bayraklarını kullanır. Ancak, bir kaynak denetimi eklentisi dizinler için "hızlı fark" işlemini desteklememe seçeneğini seçebilirler.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
