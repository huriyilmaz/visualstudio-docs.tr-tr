---
title: Yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama
description: Hangi yayımlama özelliklerinin kullanılacağı dahil olmak üzere ClickOnce uygulamanızı kullanıcılar için kullanılabilir hale getirmek için Yayımlama Sihirbazı 'Nı kullanma hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 7591513bc52807b87e9df2f0fb65364d5aff2db8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900545"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama
ClickOnce uygulamasını kullanıcılar için kullanılabilir hale getirmek için, dosyayı bir dosya paylaşımında veya yolda, FTP sunucusunda veya çıkarılabilir medyada yayımlamanız gerekir. Uygulamayı Yayımlama Sihirbazı 'nı kullanarak yayımlayabilirsiniz; Yayımlama ile ilgili ek özellikler, **Proje Tasarımcısı**' nın **Yayımla** sayfasında bulunabilir. Daha fazla bilgi için bkz. [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md).

Yayımlama Sihirbazı 'nı çalıştırmadan önce, yayımlama özelliklerini uygun şekilde ayarlamanız gerekir. Örneğin, ClickOnce uygulamanızı imzalamak için bir anahtar belirlemek isterseniz, bunu **Proje Tasarımcısı**' nın **imzalama** sayfasında yapabilirsiniz. Daha fazla bilgi için bkz. [ClickOnce uygulamalarını güvenli hale getirme](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde yükleme, uygulamanın önceki sürümlerini belirttiğiniz Yayımla konumundaki *Arşiv* adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerin temizlenmesini önler.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Bir dosya paylaşımında veya yolda yayımlamak için

1. **Çözüm Gezgini**, uygulama projesini seçin.

2. **Oluştur** menüsünde, *ProjectName* **Yayımla** ' ya tıklayın.

    Yayımla Sihirbazı görüntülenir.

3. **Uygulamayı nerede yayınlamak istiyorsunuz?** sayfasında, gösterilen biçimlerden birini kullanarak GEÇERLI bir FTP sunucu adresi veya geçerli bir dosya yolu girin ve ardından **İleri**' ye tıklayın.

4. **Kullanıcılar uygulamayı nasıl yükleyecek?** sayfasında, kullanıcıların uygulamayı yüklemek Için gidecene konum olacağını seçin:

   - Kullanıcılar bir Web sitesinden yükleyeceksiniz, **bir Web sitesinden** öğesine tıklayın ve önceki adımda girilen dosya yoluna karşılık gelen bir URL girin. **İleri**’ye tıklayın. (Bu seçenek genellikle yayımlama konumu olarak bir FTP adresi belirttiğinizde kullanılır. FTP 'den doğrudan indirme desteklenmez. Bu nedenle, buraya bir URL girmeniz gerekir.)

   - Kullanıcılar uygulamayı doğrudan dosya paylaşımından yükleya, **UNC yolu veya dosya paylaşımından** öğesine tıklayın ve ardından **İleri**' ye tıklayın. (Bu, *c:\deploy\myapp* veya *\\ \server\myapp* biçimindeki yayınlama konumlarına yöneliktir.)

   - Kullanıcılar çıkarılabilir medyadan yüklenecektir, **CD-ROM veya DVD-ROM**' d a n ' ye ve ardından **İleri**' ye tıklayın.

5. **Uygulama çevrimdışı kullanılabilir mi?** sayfasında, uygun seçeneğe tıklayın:

   - Kullanıcının ağ bağlantısı kesildiğinde uygulamanın çalıştırılmasını etkinleştirmek istiyorsanız, **Evet, bu uygulama çevrimiçi veya çevrimdışı kullanılabilir olacaktır**. Uygulama için **Başlat** menüsünde bir kısayol oluşturulur.

   - Uygulamayı doğrudan yayımlama konumundan çalıştırmak istiyorsanız Hayır ' a tıklayın **, bu uygulama yalnızca çevrimiçi olarak kullanılabilir**. **Başlat** menüsünde bir kısayol oluşturulmayacak.

     Devam etmek için **İleri**'ye tıklayın.

6. Uygulamayı yayımlamak için **son** ' a tıklayın.

    Yayımlama durumu durum bildirim alanında görüntülenir.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Bir CD-ROM veya DVD-ROM ' d e yayımlamak için

1. **Çözüm Gezgini**, uygulama projesine sağ tıklayın ve **Özellikler**' e tıklayın.

    **Proje Tasarımcısı** görüntülenir.

2. **Yayımla sekmesine tıklayarak** **Proje tasarımcısında** **Yayımla** sayfasını açın ve **Yayımla Sihirbazı** düğmesine tıklayın.

    Yayımla Sihirbazı görüntülenir.

3. **Uygulamayı nerede yayınlamak istiyorsunuz?** sayfasında, uygulamanın yayımlanacağı dosya yolunu veya FTP konumunu (örneğin, *d:\deploy*) girin. Sonra devam etmek için **İleri** ' ye tıklayın.

4. **Kullanıcılar uygulamayı nasıl yükleyecek?** sayfasında, **CD-ROM veya DVD-ROM**' d a n ' ye tıklayın ve ardından **İleri**' ye tıklayın.

   > [!NOTE]
   > CD-ROM sürücüye takıldığında yüklemenin otomatik olarak çalışmasını istiyorsanız, **Proje Tasarımcısı** ' nda **Yayımla** sayfasını açın ve **Seçenekler** düğmesine tıklayın ve ardından **Yayımlama seçenekleri** sihirbazında, CD **takıldığında kurulumu otomatik olarak Başlat**' ı seçin.

5. Uygulamanızı CD-ROM ' d e dağıtırsanız, bir Web sitesinden güncelleştirme sağlamak isteyebilirsiniz. **Uygulamanın güncelleştirmeleri denetlemesi nerede?** sayfasında, bir güncelleştirme seçeneği belirleyin:

   - Uygulama güncelleştirmeleri denetliklendiriirse, **uygulama aşağıdaki konumdan güncelleştirmeleri denetler** ve güncelleştirmelerin nakledileceği konumu girer. Bu bir dosya konumu, Web sitesi veya FTP sunucusu olabilir.

   - Uygulama güncelleştirmeleri denet, **uygulama güncelleştirmeleri denetmeyecektir** öğesine tıklayın.

     Devam etmek için **İleri**'ye tıklayın.

6. Uygulamayı yayımlamak için **son** ' a tıklayın.

    Yayımlama durumu durum bildirim alanında görüntülenir.

   > [!NOTE]
   > Yayımlama işlemi tamamlandıktan sonra, adım 3 ' te belirtilen konumdan CD-ROM veya DVD-ROM medyasına dosya kopyalamak için bir CD-Rewriter veya DVD-Rewriter kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)