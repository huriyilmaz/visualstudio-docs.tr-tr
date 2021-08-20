---
title: ClickOnce uygulamasıyla önkoşulları yükleme
description: Yüklemesi yapılan uygulamayla birlikte paket haline ClickOnce önkoşul bileşenlerini seçmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 9f319505fa0d17722e79274c993c1ccd54a8f5ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073857"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Nasıl kurulur: Bir uygulamayla önkoşulları ClickOnce yükleme
Tüm uygulamalar, çalıştırılamadan önce .NET Framework bir bilgisayara doğru sürümün yüklü olması gerekir; birçok uygulamanın da başka [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önkoşulları vardır. Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlarken, uygulamayla birlikte paket haline getirilmesi gereken bir dizi önkoşul bileşeni seçebilirsiniz. Yükleme zamanında, önceden var olup olmadığını belirlemek üzere her önkoşul için bir denetim gerçekleştirilir; yüklenmezse, uygulama yüklenmeden önce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklenir.

 Paketleme ve yayımlama önkoşulları yerine, bileşenler için bir indirme konumu da belirtebilirsiniz. Örneğin, yayımladiğiniz her uygulamaya önkoşullar dahil etmek yerine, tüm önkoşullarınızı içeren merkezi bir dosya paylaşımı veya Web konumu kullanabilirsiniz; yükleme zamanında bileşenler indirilir ve bu konumdan yüklenir.

> [!IMPORTANT]
> İlk uygulamanızı yayımlamadan önce geliştirme bilgisayarınıza önkoşul yükleyici paketleri eklemeniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gerekir. Daha fazla bilgi için, [bkz. How to: Include Prerequisites with a ClickOnce Application](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Önkoşullar, **Project** Tasarımcısı'nın Yayımla  bölmesinden **erişilebilen Önkoşullar iletişim kutusunda yönetilir.**

> [!NOTE]
> Önkoşulların önceden belirlenen listesine ek olarak, listeye kendi bileşenlerinizi de ekleyebilirsiniz. Daha fazla bilgi için [bkz. Önyükleyici paketleri oluşturma.](../deployment/creating-bootstrapper-packages.md)

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Bir uygulama ile yükleme önkoşullarını ClickOnce için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project'a** **tıklayın.**

2. Yayımla **bölmesini** seçin.

3. **Önkoşullar** düğmesine tıklayarak **Önkoşullar iletişim** kutusunu açın.

4. **Önkoşullar** iletişim kutusunda Önkoşul bileşenlerini yüklemek için kurulum programı oluştur **onay kutusunun seçili** olduğundan emin olun.

5. **Önkoşullar** listesinde, yüklemek istediğiniz bileşenleri kontrol edin ve ardından Tamam'a **tıklayın.**

     Seçilen bileşenler, uygulamanız ile birlikte paketli ve yayımlanır.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Önkoşullar için farklı bir indirme konumu belirtmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project'a** **tıklayın.**

2. Yayımla **bölmesini** seçin.

3. **Önkoşullar** düğmesine tıklayarak **Önkoşullar iletişim** kutusunu açın.

4. **Önkoşullar** iletişim kutusunda Önkoşul bileşenlerini yüklemek için kurulum programı oluştur **onay kutusunun seçili** olduğundan emin olun.

5. **Önkoşullar için yükleme konumunu belirtin bölümünde** Aşağıdaki konumdan **Önkoşulları indir'i seçin.**

6. Açılan listeden bir konum seçin veya URL, dosya yolu veya FTP konumu girin ve tamam'a **tıklayın.**

    > [!NOTE]
    > Belirtilen bileşenler için yükleyicilerin belirtilen konumda mevcut olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)