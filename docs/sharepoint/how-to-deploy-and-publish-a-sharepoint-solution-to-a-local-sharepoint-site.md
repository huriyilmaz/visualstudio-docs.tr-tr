---
title: '& SharePoint çözümünü yerel SharePoint sitesine dağıtma ve yayımlama'
titleSuffix: ''
description: geliştirme bilgisayarınızda yerel bir SharePoint sunucusuna SharePoint çözümleri dağıtmayı veya yayımlamayı inceleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0ca33017e48db24a4f1ab055289683737d047c4e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636862"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>nasıl yapılır: SharePoint çözümünü yerel SharePoint sitesine dağıtma ve yayımlama
  geliştirme bilgisayarınızda yerel bir SharePoint sunucusuna SharePoint çözümleri dağıtabilir veya yayımlayabilirsiniz. dağıtım işlemi *. wsp* dosyasını SharePoint sunucusuna kopyalar, çözümü yüklerse ve sonra özellikleri etkinleştirir. yayımlama işlemi yalnızca *. wsp* dosyasını SharePoint sunucusuna kopyalar ve onu kurar. SharePoint etkinleştirmek için el ile etkinleştirmeniz gerekir.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>yerel SharePoint sunucusuna bir SharePoint çözümü dağıtmak için

1. **Çözüm Gezgini**, dağıtmak istediğiniz projeyi seçin.

2. Menü çubuğunda **Oluştur**, **Çözümü dağıt**' ı seçin.

     *. wsp* dosyası oluşturulur ve yerel SharePoint sunucusuna yüklenir. Ayrıca, Özellikler etkinleştirilir.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>SharePoint çözümünü yerel SharePoint sunucusuna yayımlamak için

1. **Çözüm Gezgini**, yayımlamak istediğiniz SharePoint projesi için kısayol menüsünü açın ve ardından **yayımla**' yı seçin.

2. **Yayımla** Iletişim kutusunda **dosya sistemine yayınla** seçenek düğmesini seçin.

3. **Hedef konum** metin kutusuna bir yerel yol girin ve ardından **Yayınla** düğmesini seçin.

     yayımlama ilerlemesi Visual Studio **çıkış** penceresinde görüntülenir. işlem tamamlandığında, çözüm (*. wsp*) dosyası yerel SharePoint sunucusuna yüklenir. Ancak, hala SharePoint kullanılmak üzere etkinleştirilmesi gerekir. Çözüm dosyası zaten varsa, bir hata oluşur ve var olan dosyanın üzerine yazmak isteyip istemediğinizi sorar. paketi yükseltme hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)konusunda uzak paketleri yükseltme bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [nasıl yapılır: SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
