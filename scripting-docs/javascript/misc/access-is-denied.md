---
description: Komut dosyası, geçerli sayfanın ana bilgisayarı dışında bir kaynaktan verilere erişmeye çalıştı.
title: Erişim reddedildi | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571941"
---
# <a name="access-is-denied"></a>Erişim reddedildi
Komut dosyası, geçerli sayfanın ana bilgisayarı dışında bir kaynaktan verilere erişmeye çalıştı. Aynı kaynak Ilkesi ve ardından Internet Explorer ve diğer tarayıcılar, betiklerin yalnızca aynı düzen, ana bilgisayar ve geçerli sayfanın URL 'sini içeren kaynaklardan verilere erişmesine olanak tanır.  
  
 Örneğin, geçerli sayfa ise `https://employees.mycompany.com` aşağıdaki URL 'lerden verilere erişemezsiniz:  
  
- `http://data.contoso.com`HTTPS yerine HTTP kullandığından.  
  
- `https://somedatasource.com`farklı bir etki alanı olduğundan.  
  
- `https://employees.mycompany.com:8888`farklı bir bağlantı noktası kullandığından.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Çağrıya çalıştığınız API 'nin, karşılıklı kaynak komut dosyasına güvenle izin veren iki yaklaşım olan JSONP veya CORS 'yi destekleyip desteklemediğini araştırın.  
  
- Bir REST API çağırmaya çalışıyorsanız, bu çağrıyı sunucu tarafı kodunuza yeniden düzenleyin ve ardından istemci tarafı betikleriniz için yeni bir REST uç noktası sunun.  
  
     Ek bilgi için, aynı kaynak Ilkesi, JSONP ve CORS ile ilgili çevrimiçi belgeleri arayın.
