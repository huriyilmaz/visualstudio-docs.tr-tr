---
title: Yayımlama ClickOnce kullanarak uygulama yayımlama
description: Yayımla Sihirbazı'nı kullanarak, ClickOnce yayımlama özelliklerini kullanıcılar için kullanılabilir hale nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 195dc94991def92e1612e7f1752d348e1eb8d578
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089972"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama
Bir uygulamanın ClickOnce için bir dosya paylaşımında, yolda, FTP sunucusunda veya çıkarılabilir medyada yayımlamanız gerekir. Yayımlama Sihirbazı'nı kullanarak uygulamayı yayımlayın; yayımlamayla ilgili ek özellikler,  Project **Designer'ın Yayımla sayfasında mevcuttur.** Daha fazla bilgi için [bkz. ClickOnce yayımlama.](../deployment/publishing-clickonce-applications.md)

Yayımlama Sihirbazı'nı çalıştırmadan önce yayımlama özelliklerini uygun şekilde ayarlayabilirsiniz. Örneğin, uygulama uygulamanıza imzalamak için bir anahtar ClickOnce, bunu Project **Tasarımcısı'nın İmzalama sayfasında bulabilirsiniz.**  Daha fazla bilgi için [bkz. Güvenli ClickOnce.](../deployment/securing-clickonce-applications.md)

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yükleyebilirsiniz. Yükleme, uygulamanın önceki sürümlerini belirttiğiniz yayımlama konumu olan *Arşiv* adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerden uzak tutar.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'ye** tıklayın. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="to-publish-to-a-file-share-or-path"></a>Bir dosya paylaşımına veya yola yayımlamak için

1. Uygulama **Çözüm Gezgini** uygulama projesini seçin.

2. Derleme menüsünde **Proje** Adını **Yayımla'ya** *tıklayın.*

    Yayımlama Sihirbazı görüntülenir.

3. Uygulamayı **nerede yayımlamak istiyorsunuz?** sayfasında, gösterilen biçimlerden birini kullanarak geçerli bir FTP sunucusu adresi veya geçerli bir dosya yolu girin ve ardından Sonraki 'ye **tıklayın.**

4. Kullanıcılar **uygulamayı nasıl yükleyecek?** sayfasında, kullanıcıların uygulamayı yüklemek için gideceği konumu seçin:

   - Kullanıcılar bir Web sitesinden yüklenirse, **Bir Web** sitesinden'e tıklayın ve önceki adımda girilen dosya yoluna karşılık gelen bir URL girin. **İleri**’ye tıklayın. (Bu seçenek genellikle yayımlama konumu olarak bir FTP adresi belirttiğinizde kullanılır. FTP'den doğrudan indirme desteklenmiyor. Bu nedenle buraya bir URL girmeniz gerekir.)

   - Kullanıcılar uygulamayı doğrudan dosya paylaşımından yükleyecekse, **BIR UNC** yolundan veya dosya paylaşımından'a ve ardından Sonraki 'ye **tıklayın.** (Bu, *c:\deploy\myapp* veya *\\ \server\myapp formunun konumlarını yayımlamaya yöneliktir.)*

   - Kullanıcılar çıkarılabilir medyadan yüklenecekse, **BIR CD-ROM veya DVD-ROM'dan'a** ve ardından Sonraki'ye **tıklayın.**

5. Uygulama **çevrimdışı kullanılabilir mi? sayfasında,** uygun seçeneği tıklatın:

   - Kullanıcının ağ bağlantısı kesildiğinde uygulamanın çalışmasına olanak sağlamak istiyorsanız Evet'e tıklayın, bu uygulama çevrimiçi **veya çevrimdışı kullanılabilir olur.** Uygulama için **Başlat** menüsünde bir kısayol oluşturulur.

   - Uygulamayı doğrudan yayımlama konumdan çalıştırmak için Hayır, bu uygulama yalnızca **çevrimiçi kullanılabilir'e tıklayın.** Başlat menüsünde **bir** kısayol oluşturulmaz.

     Devam etmek için **İleri**'ye tıklayın.

6. Uygulamayı **yayımlamak** için Son'a tıklayın.

    Yayımlama durumu, durum bildirim alanında görüntülenir.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>CD-ROM veya DVD-ROM'a yayımlamak için

1. Uygulama **Çözüm Gezgini,** uygulama projesine sağ tıklayın ve Özellikler'e **tıklayın.**

    Project **Tasarımcısı** görüntülenir.

2. Yayımla **sekmesine** tıklayarak  Project **Tasarımcısı'nda** Yayımla sayfasını açın ve Yayımla Sihirbazı **düğmesine** tıklayın.

    Yayımlama Sihirbazı görüntülenir.

3. Uygulamayı **nerede yayımlamak istiyorsunuz?** sayfasında, uygulamanın yayımlanacak dosya yolunu veya FTP konumunu girin, örneğin *d:\deploy*. Ardından devam etmek **için Sonraki'ne** tıklayın.

4. Kullanıcılar uygulamayı **nasıl yükleyecek?** sayfasında, **BIR CD-ROM veya DVD-ROM'dan'a** ve ardından Sonraki 'ye **tıklayın.**

   > [!NOTE]
   > Cd-ROM sürücüye eklenirken yüklemenin otomatik olarak çalışmasına izin  verdiyebilirsiniz, **Project Tasarımcısı'nda** Yayımla sayfasını açın  ve Seçenekler düğmesine tıklayın ve ardından Yayımlama Seçenekleri sihirbazında CD yüklemeleri **için'yi seçin, CD** ekli olduğunda Kurulumu otomatik olarak başlatın. 

5. Cd-ROM üzerinde uygulama dağıtırsanız, bir Web sitesinden güncelleştirmeler sağlamak istiyor olabilir. Uygulama **güncelleştirmeleri nerede kontrol ediyor?** sayfasında bir güncelleştirme seçeneği belirleyin:

   - Uygulama güncelleştirmeleri kontrol ediyorsa, **Uygulama** güncelleştirmeleri aşağıdaki konumdan kontrol edin ve güncelleştirmelerin yayınlay olduğu konumu girin. Bu bir dosya konumu, Web sitesi veya FTP sunucusu olabilir.

   - Uygulama güncelleştirmeleri denetlemezse Uygulama güncelleştirmeleri **denetlemez'e tıklayın.**

     Devam etmek için **İleri**'ye tıklayın.

6. Uygulamayı **yayımlamak** için Son'a tıklayın.

    Yayımlama durumu, durum bildirim alanında görüntülenir.

   > [!NOTE]
   > Yayımlama tamamlandıktan sonra, dosyaları 3. adımda belirtilen CD-Rewriter veya DVD-ROM medya DVD-Rewriter kopyalamak için bir CD-Rewriter veya DVD-Rewriter dosyası kullanmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Office kullanarak bir Office çözümü ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)