---
title: CD Yüklemeleri için AutoStart'i | Microsoft Docs
description: CD-ROM veya DVD-ROM gibi çıkarılabilir medya ClickOnce bir uygulama dağıtırken AutoStart'ı etkinleştirmeyi öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f16def763bebca4cc91b902d1f9202c6a6fdaede
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127928"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Nasıl olur: CD yüklemeleri için AutoStart'i etkinleştirme
Bir uygulamayı CD-ROM veya DVD-ROM gibi çıkarılabilir medya üzerinden dağıtırken, medya eklenirken uygulamanın otomatik olarak başlatılabilir şekilde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] etkinleştirebilirsiniz.

 `AutoStart`, Project **Designer'ın Yayımla sayfasında etkinleştirilebilir.** 

### <a name="to-enable-autostart"></a>AutoStart'i etkinleştirmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project** **tıklayın.**

2. Yayımla **sekmesine** tıklayın.

3. Seçenekler **düğmesine** tıklayın.

     Yayımlama **Seçenekleri iletişim** kutusu görüntülenir.

4. **Dağıtım'a tıklayın.**

5. CD **yüklemeleri için, CD ekildiğinde Kurulumu otomatik olarak başlat onay** kutusunu seçin.

     *Autorun.inf* dosyası, uygulama yayımlanırken yayımlama konuma kopyalanır.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)