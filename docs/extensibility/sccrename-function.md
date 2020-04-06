---
title: SccRename Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700424"
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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpFileName

[içinde] Yeniden adlandırılacak dosyanın tam nitelikli dosya adı.

 lpNewName

[içinde] Tam nitelikli yeni isim. Dizin yolu farklıysa, dosya bir alt dizimden diğerine taşınmıştır.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Yeniden adlandırma işlemi başarıyla tamamlandı.|
|SCC_E_PROJNOTOPEN|Proje kaynak denetimi altında açık değil.|
|SCC_E_FILENOTCONTROLLED|Dosya kaynak denetimi altında değil.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi tamamlama yetkisi yoktur.|
|SCC_E_COULDNOTCREATEPROJECT|Proje yeniden adlandırma işleminin bir parçası olarak oluşturulamadı.|
|SCC_E_OPNOTPERFORMED|İşlem gerçekleştirilmedi.|
|SCC_E_NONSPECIFICERROR|Belirtilmeyen veya genel bir hata oluştu.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev, bir dosyayı yeniden adlandırmak veya kaynak denetim sisteminde bir konumdan diğerine taşımak için kullanılabilir. Kaynak denetimi eklentisi diskteki dosyaya erişmeye çalışmamalıdır. Yerel dosyayı yeniden adlandırmak IDE'nin sorumluluğundadır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
