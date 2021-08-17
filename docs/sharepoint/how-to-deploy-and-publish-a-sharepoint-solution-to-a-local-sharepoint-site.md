---
title: Bir & yerel SharePoint sitesinde yayımlamak için SharePoint dağıtma
titleSuffix: ''
description: Geliştirme bilgisayarınızda yerel bir SharePoint çözüm dağıtmayı veya SharePoint yayımlamayı gözden geçirme.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047718"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Nasıl SharePoint: Yerel SharePoint çözümü dağıtma ve yayımlama
  Geliştirme çözümlerinizi geliştirme SharePoint yerel bir SharePoint sunucuya dağıtabilirsiniz veya yayımlayın. Dağıtım işlemi , *.wsp* dosyasını SharePoint sunucusuna kopyalar, çözümü yüklür ve ardından özellikleri etkinleştirir. Yayımlama işlemi yalnızca *.wsp dosyasını* SharePoint sunucuya kopyalar ve bunu yüklür. Bu özelliği etkin bir şekilde etkinleştirmek için el ile SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Yerel SharePoint sunucusuna bir çözüm SharePoint için

1. Bu **Çözüm Gezgini** içinde, dağıtmak istediğiniz projeyi seçin.

2. Menü çubuğunda Derleme, Çözüm **Dağıtma'ya tıklayın.**

     *.wsp* dosyası oluşturulur ve yerel sunucuya SharePoint yüklenir. Ayrıca, özellikler etkinleştirilir.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Yerel bir SharePoint sunucusuna bir çözüm SharePoint için

1. Bu **Çözüm Gezgini,** yayımlamak istediğiniz SharePoint projesinin kısayol menüsünü açın ve yayımla'yı **seçin.**

2. Yayımla **iletişim** kutusunda Dosya Sisteminde **Yayımla seçeneğini** belirleyin.

3. Hedef **Konum metin** kutusuna yerel bir yol girin ve ardından Yayımla **düğmesini** seçin.

     Yayımlama ilerleme durumu Çıkış penceresinde Visual Studio **görüntülenir.** İşlem tamamlandığında çözüm (*.wsp*) dosyası yerel sunucuya SharePoint yüklenir. Ancak, yine de bu bek bir SharePoint. Çözüm dosyası zaten varsa bir hata oluşur ve var olan dosyanın üzerine yazmak isteyip istemediğinizi sorar. Paketi yükseltme hakkında daha fazla bilgi için, Uzak bir sunucuda uzak paketleri yükseltme: Uzak bir sunucu üzerinde dağıtım, yayımlama ve SharePoint yükseltme bölümündeki [bölümüne bakın.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Uzak bir sunucuda SharePoint, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Çözüm SharePoint paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl SharePoint: SharePoint paketi özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl kullanılır: Paket Tasarımcısını kullanarak pakete özellik ve öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
