---
description: Bu işlev, kaynak denetim sistemindeki bir dosyayı yeniden adlandırır.
title: SccRename Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f9085d764378c5e0743d239b3bde427befffb2d7cf1945f9ce8fa054ea780af4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359006"
---
# <a name="sccrename-function"></a>SccRename İşlevi
Bu işlev, kaynak denetim sistemindeki bir dosyayı yeniden adlandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 lendiği

'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.

 lpFileName

'ndaki Yeniden adlandırılan dosyanın tam dosya adı.

 Lpyeniad

'ndaki Tam nitelikli yeni ad. Dizin yolu farklıysa, dosya bir alt dizinden diğerine taşınır.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Yeniden adlandırma işlemi başarıyla tamamlandı.|
|SCC_E_PROJNOTOPEN|Proje, kaynak denetimi altında açık değil.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu.|
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi tamamlamaya yetkili değil.|
|SCC_E_COULDNOTCREATEPROJECT|Proje, yeniden adlandırma sürecinin bir parçası olarak oluşturulamadı.|
|SCC_E_OPNOTPERFORMED|İşlem gerçekleştirilmedi.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, kaynak denetim sisteminde bir dosyayı yeniden adlandırmak veya bir konumdan diğerine taşımak için kullanılabilir. Kaynak denetimi eklentisinin diskteki dosyaya erişmeyi denememelidir. Bu, yerel dosyayı yeniden adlandırmak için IDE 'nin sorumluluğundadır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
