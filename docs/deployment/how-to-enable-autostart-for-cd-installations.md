---
title: CD yüklemeleri için AutoStart 'ı etkinleştirme | Microsoft Docs
description: Bir ClickOnce uygulamasını, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıttığınızda otomatik başlatmayı nasıl etkinleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f6ed3df72b98454c4669e7d9bcd21c0612a6fef3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349964"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Nasıl yapılır: CD yüklemeleri için AutoStart 'ı etkinleştirme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama, CD-ROM veya DVD-ROM gibi çıkarılabilir medya aracılığıyla dağıtıldığında, `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] medya takıldığında uygulamanın otomatik olarak başlatılmasını sağlayabilirsiniz.

 `AutoStart`, **Proje Tasarımcısı** ' nın **Yayımla** sayfasında etkinleştirilebilir.

### <a name="to-enable-autostart"></a>AutoStart 'ı etkinleştirmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Seçenekler** düğmesine tıklayın.

     **Yayımlama seçenekleri** iletişim kutusu görüntülenir.

4. **Dağıtım** ' ye tıklayın.

5. CD **takıldığında kurulumu otomatik olarak Başlat** onay kutusunu seçin.

     Uygulama yayımlandığında bir *Autorun. inf* dosyası yayımlama konumuna kopyalanır.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)