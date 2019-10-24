---
title: 'IDiaFrameData:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c9af8293dfc6a35e5f0e42d9596494d74b10aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743690"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Yığın geri sarma gerçekleştirir ve sonuçları bir yığın ilerleme çerçevesi arabiriminde döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametreler
 `frame`

'ndaki Çerçeve yazmaçlarının durumunu tutan bir [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_DIA_INPROLOG|Prolog kodu sırasında yığın çerçevesi yürütülemiyor.|
|E_DIA_SYNTAX|Çerçeve programında ayrıştırma hatasıyla karşılaşıldı.|
|E_DIA_FRAME_ACCESS|Kayıt defterlerine veya belleğe erişilemiyor.|
|E_DIA_VALUE|Değerin hesaplamasında hata oluştu (örneğin, sıfıra bölme).|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yığın geri yüklenirken hata ayıklama sırasında çağrılır. [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) nesnesi, kayıt güncelleştirmelerini almak ve `execute` yöntemi tarafından kullanılan yöntemleri sağlamak için istemci uygulama tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)