---
title: SharePoint çözümünü yerel SharePoint sitesine dağıtma & yayımlama
titleSuffix: ''
description: Geliştirme bilgisayarınızda SharePoint çözümlerini yerel bir SharePoint sunucusuna dağıtmayı veya yayımlamayı inceleyin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65683544f345a2378fdec559f582985ffec7bc43
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903591"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Nasıl yapılır: bir SharePoint çözümünü yerel bir SharePoint sitesine dağıtma ve yayımlama
  Geliştirme bilgisayarınızda, SharePoint çözümlerini yerel bir SharePoint sunucusuna dağıtabilir veya yayımlayabilirsiniz. Dağıtım işlemi *. wsp* dosyasını SharePoint sunucusuna kopyalar, çözümü yüklenir ve ardından özellikleri etkinleştirir. Yayımlama işlemi yalnızca *. wsp* dosyasını SharePoint sunucusuna kopyalar ve onu kurar. SharePoint 'te etkinleştirmek için el ile etkinleştirmeniz gerekir.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Bir SharePoint çözümünü yerel SharePoint sunucusuna dağıtmak için

1. **Çözüm Gezgini**, dağıtmak istediğiniz projeyi seçin.

2. Menü çubuğunda **Oluştur**, **Çözümü dağıt**' ı seçin.

     *. Wsp* dosyası oluşturulur ve yerel SharePoint sunucusunda yüklüdür. Ayrıca, Özellikler etkinleştirilir.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Bir SharePoint çözümünü yerel bir SharePoint sunucusuna yayımlamak için

1. **Çözüm Gezgini**' de, yayımlamak istediğiniz SharePoint projesinin kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

2. **Yayımla** Iletişim kutusunda **dosya sistemine yayınla** seçenek düğmesini seçin.

3. **Hedef konum** metin kutusuna bir yerel yol girin ve ardından **Yayınla** düğmesini seçin.

     Yayımlama ilerlemesi, Visual Studio **çıktı** penceresinde görünür. İşlem tamamlandığında, çözüm (*. wsp*) dosyası yerel SharePoint sunucusuna yüklenir. Ancak, hala SharePoint 'te kullanılmak üzere etkinleştirilmelidir. Çözüm dosyası zaten varsa, bir hata oluşur ve var olan dosyanın üzerine yazmak isteyip istemediğinizi sorar. Paketi yükseltme hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)konusunda uzak paketleri yükseltme bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
