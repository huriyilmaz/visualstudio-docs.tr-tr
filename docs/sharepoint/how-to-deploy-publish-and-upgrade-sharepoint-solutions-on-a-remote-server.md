---
title: Dağıtım, yayımlama, & çözümleri uzaktan SharePoint yükseltme
titleSuffix: ''
description: Korumalı alanlı çözümleri uzak bir SharePoint veya yerel bir site üzerinde dağıtın, yayımlayın ve SharePoint yükseltin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: fb4838625029a95f2c7b6d55cfba22284c168818
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084291"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Nasıl kullanılır: Uzak bir sunucuda SharePoint, yayımlama ve yükseltme
  Sanal çözümleri yerel SharePoint dağıtmaya ek olarak, korumalı alanlı SharePoint çözümlerini uzak sitelere veya yerel sitelere SharePoint yayımabilirsiniz. Uzaktan yayımlama işlemi *.wsp* dosyasını SharePoint sunucusuna kopyalar, çözümü yüker ve ardından çözümü etkinleştirmenizi sağlar. Ayrıca, uzak bir SharePoint çözümü yüklemesini, değişiklikler yapıldıktan sonra yükseltebilirsiniz.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Korumalı alanlı bir SharePoint uzak bir SharePoint sunucusuna yayımlamak için

1. Bu **Çözüm Gezgini,** yayımlamak istediğiniz korumalı SharePoint projesinin kısayol menüsünü açın ve yayımla'yı **seçin.**

2. Yayımla **iletişim** kutusunda, SharePoint **Sitesinde** Yayımla seçeneğini belirleyin ve ardından bir çevrimiçi yayımlama sitesinin URL'sini girin, örneğin: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Yayımlandıktan **sonra Çözüm Galerisi sayfasında** çözüm listesini görüntülemek için Yayımlama sonrasında tarayıcıda Çözüm Galerisi sayfasını aç **seçeneğini** belirleyin.

4. Yayımla **düğmesini** seçin.

5. Kullanıcı kimlik doğrulaması gerekli ise uzak sunucuda oturum açma.

     Yayımlama ilerleme durumu Çıkış penceresinde Visual Studio **görüntülenir.** İşlem tamamlandığında çözüm (*.wsp*) dosyası uzak sunucuya SharePoint yüklenir. Ancak, daha önce SharePoint.

6. Çözüm **Galerisi sayfasında,** SharePoint seçin ve şeritte Etkinleştir **düğmesini** seçin.

7. Çözümü **Etkinleştir iletişim** kutusundaki şeritte Etkinleştir düğmesini **yeniden** seçin.

     Çözüm **Galerisi** sayfasındaki **Durum sütunu,** uygulamanın etkin olduğunu gösterir.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Uzak bir sunucu üzerinde korumalı SharePoint çözümü SharePoint için
 Korumalı alan SharePoint bir uzak sunucuda zaten yayımlanmışsa, aşağıdaki işlem uygulamasında uygulamada değişiklik yaptıktan sonra bunu yükseltmenizi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sağlar.

1. içinde SharePoint paketini yeniden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adlandırabilirsiniz. Bunu yapmak için **Çözüm Gezgini** açın. Paket **Gezgini'nde görünür.**

2. Paket **Gezgini'nde,** **Ad** kutusunda, paket adını benzersiz bir adla değiştirebilirsiniz.

3. Projeyi kaydedin.

4. Bu **Çözüm Gezgini** proje kısayol menüsünü açın ve Yayımla'yı **seçin.**

5. Yayımla **iletişim** kutusunda, **SharePoint Sitesinde** Yayımla seçeneği düğmesini seçin ve çözümün kayded olduğu uzak sunucunun URL'si eksikse girin.

6. Yayımlandıktan **sonra Çözüm Galerisi sayfasında** çözüm listesini görüntülemek için Yayımlama sonrasında tarayıcıda Çözüm Galerisi sayfasını aç **seçeneğini** belirleyin.

7. Yayımla **düğmesini** seçin.

8. Kullanıcı kimlik doğrulaması gerekli ise uzak sunucuda oturum açma.

     Uzak sunucuda kısa süre önce oturum açtıysanız kimlik doğrulaması gerekli olabilir.

     Uygulamanın aynı adı içeren eski sürümü SharePoint sunucusunda hala mevcutsa, SharePoint sunucusunda aynı adı içeren bir paketin zaten var olduğunu SharePoint alırsınız. Yayımlamadan önce paketi benzersiz bir adla yeniden adlandırmalısiniz.

9. Yeni uygulamayı SharePoint seçin ve ardından şeritte Yükselt **düğmesini** seçin.

10. Çözümü **Yükselt iletişim** kutusundaki şeritte Yükselt düğmesini **yeniden** seçin. Çözüm **Galerisi** sayfasındaki **Durum sütunu** artık uygulamanın etkin olduğunu belirtmektedir.

     Çözümün eski sürümü devre dışı bırakılır, çözümün yeni sürümü eski çözümden sürdürülen verilerle yükseltilir ve yeni çözüm, SharePoint.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl SharePoint: Yerel SharePoint çözümü dağıtma ve yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Çözüm SharePoint paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl SharePoint: SharePoint paketi özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl kullanılır: Paket Tasarımcısını kullanarak pakete özellik ve öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
