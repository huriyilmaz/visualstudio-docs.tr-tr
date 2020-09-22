---
title: CD yüklemeleri için AutoStart 'ı etkinleştirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fa4830c3ea5ff840e0d58f6d31f718c28ec3fb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850949"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Nasıl yapılır: CD yüklemeleri için AutoStart 'ı etkinleştirme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıtıldığında, `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] medya takıldığında uygulamanın otomatik olarak başlatılmasını sağlayabilirsiniz.

 `AutoStart`, **Proje Tasarımcısı**' nın **Yayımla** sayfasında etkinleştirilebilir.

### <a name="to-enable-autostart"></a>AutoStart 'ı etkinleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Seçenekler** düğmesine tıklayın.

     **Yayımlama seçenekleri** iletişim kutusu görüntülenir.

4. **Dağıtım**' ye tıklayın.

5. CD **takıldığında kurulumu otomatik olarak Başlat** onay kutusunu seçin.

     Uygulama yayımlandığında bir *Autorun. inf* dosyası yayımlama konumuna kopyalanır.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)