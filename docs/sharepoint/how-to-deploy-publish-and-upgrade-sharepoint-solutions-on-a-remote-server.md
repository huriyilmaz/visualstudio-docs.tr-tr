---
title: SharePoint çözümlerini uzaktan dağıtın, yayımlayın & yükseltin
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f05f42f8aed35696b962e71a5fce86c2956b3661
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016804"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme
  SharePoint çözümlerini yerel sisteme dağıtmanın yanı sıra, korumalı SharePoint çözümlerini uzak sitelere veya yerel SharePoint sitelerine de yayımlayabilirsiniz. Uzaktan yayımlama işlemi, *. wsp* dosyasını SharePoint sunucusuna kopyalar, çözümü yüklüyor ve sonra çözümü etkinleştirmenizi sağlar. Ayrıca, bir uzak SharePoint çözüm yüklemesini değişiklikler yapıldıktan sonra yükseltebilirsiniz.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Korumalı bir SharePoint çözümünü uzak bir SharePoint sunucusuna yayımlamak için

1. **Çözüm Gezgini**' de, yayımlamak Istediğiniz korumalı SharePoint projesinin kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

2. **Yayımla** iletişim kutusunda, **SharePoint sitesine yayımla** seçenek düğmesini seçin ve ardından çevrimiçi YAYıMLAMA sitesi için bir URL girin, örneğin: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Yayımladıktan sonra **Çözüm Galerisi** sayfasında çözümlerin listesini görüntülemek için, **yayımlamadan sonra tarayıcıda Çözüm Galerisi sayfasını aç** seçenek düğmesini seçin.

4. **Yayımla** düğmesini seçin.

5. Kullanıcı kimlik doğrulaması gerekliyse uzak sunucuda oturum açın.

     Yayımlama ilerlemesi, Visual Studio **çıktı** penceresinde görünür. İşlem tamamlandığında, çözüm (*. wsp*) dosyası uzak SharePoint sunucusuna yüklenir. Ancak, SharePoint 'te kullanılmadan önce yine de etkinleştirilmesi gerekir.

6. **Çözüm Galerisi** sayfasında, SharePoint uygulamasını seçin ve ardından şeritte **Etkinleştir** düğmesini seçin.

7. **Çözümü etkinleştir** iletişim kutusunda, şeritte, **Etkinleştir** düğmesini yeniden seçin.

     **Çözüm Galerisi** sayfasındaki **durum** sütunu, uygulamanın etkin olduğunu gösterir.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Uzak SharePoint sunucusunda korumalı bir SharePoint çözümünü yükseltmek için
 Korumalı bir SharePoint çözümü, uzak bir sunucuda zaten yayımlanıyorsa, ' de uygulamada değişiklik yaptıktan sonra aşağıdaki işlem bunu yükseltmenizi sağlar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. İçindeki SharePoint paketini yeniden adlandırın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bunu yapmak için **Çözüm Gezgini** ' de paketi açın. **Paket Gezgini**'nde görünür.

2. **Paket Gezgini**' nde, **ad** kutusunda, paket adını benzersiz bir adla değiştirin.

3. Projeyi kaydedin.

4. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

5. **Yayımla** iletişim kutusunda, **SharePoint sitesine yayımla** seçenek düğmesini seçin ve ardından çözümün kaydedildiği uzak sunucunun URL 'si eksikse, girin.

6. Yayımladıktan sonra **Çözüm Galerisi** sayfasında çözümlerin listesini görüntülemek için, **yayımlamadan sonra tarayıcıda Çözüm Galerisi sayfasını aç** seçenek düğmesini seçin.

7. **Yayımla** düğmesini seçin.

8. Kullanıcı kimlik doğrulaması gerekliyse uzak sunucuda oturum açın.

     Yakın zamanda uzak sunucuda oturum açtıysanız, kimlik doğrulaması gerekli olmayabilir.

     Uygulamanın aynı ada sahip eski sürümü SharePoint sunucusunda hala mevcutsa, SharePoint sunucusunda aynı ada sahip bir paketin zaten var olduğunu belirten bir hata alırsınız. Yayımlamadan önce paketi benzersiz bir adla yeniden adlandırmanız gerekir.

9. SharePoint 'te yeni uygulamayı seçin ve ardından şeritte **Yükselt** düğmesini seçin.

10. **Çözümü Yükselt** iletişim kutusunda, şeritte, **Yükselt** düğmesini yeniden seçin. **Çözüm Galerisi** sayfasındaki **durum** sütunu artık uygulamanın etkin olduğunu göstermelidir.

     Çözümün eski sürümü devre dışı bırakıldı, çözümün yeni sürümü eski çözümden korunan verilerle yükseltilir ve yeni çözüm SharePoint 'te etkinleştirilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint çözümünü yerel bir SharePoint sitesine dağıtma ve yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
