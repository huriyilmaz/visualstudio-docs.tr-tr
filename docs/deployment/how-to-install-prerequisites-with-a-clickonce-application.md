---
title: ClickOnce uygulaması ile önkoşulları nasıl yüklenir | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4ad97439d330a6fc51e741e9ea05ef53a5798a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382386"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek
Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar, çalıştırılmadan önce bir bilgisayara .NET Framework 'nin doğru sürümünün yüklü olmasını gerektirir; birçok uygulamanın da başka önkoşulları da vardır. Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , uygulamanızla birlikte paketlenebilmeniz için bir önkoşul bileşenleri kümesi seçebilirsiniz. Yükleme zamanında, her önkoşul için, zaten mevcut olup olmadığını belirlemede bir denetim gerçekleştirilecek. Aksi takdirde, uygulama yüklenmeden önce yüklenir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Paketleme ve yayımlama önkoşulları yerine, bileşenler için de bir indirme konumu belirtebilirsiniz. Örneğin, yayımladığınız her uygulamayla önkoşulları dahil etmek yerine, tüm önkoşulların yükleyicilerinin bulunduğu merkezi bir dosya paylaşımından veya Web konumundan (yükleme zamanında), bileşenler indirilir ve bu konumdan yüklenir.

> [!IMPORTANT]
> İlk uygulamanızı yayımlamadan önce geliştirme bilgisayarınıza önkoşul Yükleyici paketleri eklemeniz gerekir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: önkoşulları ClickOnce uygulamasıyla ekleme](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Önkoşullar, **Proje Tasarımcısı**' nın **Yayımla** bölmesinden erişilebilen **Önkoşullar** iletişim kutusunda yönetilir.

> [!NOTE]
> Önkoşul listesine ek olarak, kendi bileşenlerinizi listeye ekleyebilirsiniz. Daha fazla bilgi için bkz. [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>ClickOnce uygulamasıyla yüklenecek önkoşulları belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** bölmesini seçin.

3. **Önkoşullar iletişim kutusunu** açmak için **Önkoşullar** düğmesine tıklayın.

4. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

5. **Önkoşullar** listesinde, yüklemek istediğiniz bileşenleri işaretleyin ve ardından **Tamam**' a tıklayın.

     Seçili bileşenler paketlenecektir ve uygulamanızla birlikte yayımlanır.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Önkoşullar için farklı bir indirme konumu belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** bölmesini seçin.

3. **Önkoşullar iletişim kutusunu** açmak için **Önkoşullar** düğmesine tıklayın.

4. **Önkoşullar** iletişim kutusunda, **Önkoşul bileşenlerini yüklemek Için Kurulum programı oluştur** onay kutusunun işaretli olduğundan emin olun.

5. **Önkoşullar için yükleme konumunu belirtin** bölümünde, **aşağıdaki konumdan önkoşulları indir**' i seçin.

6. Açılan listeden bir konum seçin veya bir URL, dosya yolu veya FTP konumu girin ve ardından Tamam ' a tıklayın **.**

    > [!NOTE]
    > Belirtilen bileşenler için yükleyicilerin belirtilen konumda mevcut olduğundan emin olmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)