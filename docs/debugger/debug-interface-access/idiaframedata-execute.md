---
title: 'IDiaFrameData:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2587d10b613200b1bf850636f613abbb497e04de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467451"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Yığın geri sarma gerçekleştirir ve sonuçları bir yığın ilerleme çerçevesi arabiriminde döndürür.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametreler
 `frame`

'ndaki Çerçeve yazmaçlarının durumunu tutan bir [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bu yöntem için olası dönüş değerleri gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|E_DIA_INPROLOG|Prolog kodu sırasında yığın çerçevesi yürütülemiyor.|
|E_DIA_SYNTAX|Çerçeve programında ayrıştırma hatasıyla karşılaşıldı.|
|E_DIA_FRAME_ACCESS|Kayıt defterlerine veya belleğe erişilemiyor.|
|E_DIA_VALUE|Değerin hesaplamasında hata oluştu (örneğin, sıfıra bölme).|

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, yığın geri yüklenirken hata ayıklama sırasında çağrılır. [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) nesnesi, kayıt güncelleştirmelerini almak ve yöntemi tarafından kullanılan yöntemleri sağlamak için istemci uygulama tarafından uygulanır `execute` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)