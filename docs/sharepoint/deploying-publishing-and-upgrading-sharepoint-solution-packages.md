---
title: SharePoint çözüm paketlerini dağıtma, yayımlama & yükseltme
description: SharePoint çözüm paketlerini dağıtın, yayımlayın ve yükseltin. Dağıtım işlemini özelleştirin. Paketleri uzak veya yerel bir sunucuya yayımlayın.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: ab97efc82575c31c8e05b73063c2b53a09691d2d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672671"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme
  Visual Studio 'da bir SharePoint çözümü geliştirdikten sonra, paket (. wsp) dosyasını yerel bir SharePoint sunucusuna dağıtabilir veya uzak ya da yerel bir SharePoint sunucusunda yayımlayabilirsiniz. Dosyaları dağıtırsanız, paket dosyalarının (. wsp) nasıl dağıtıldığını özelleştirebilirsiniz.

> [!NOTE]
> Şu anda, uzak SharePoint sunucularında yalnızca korumalı çözümler yayımlanabilir. Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Dağıtma, yayımlama ve yükseltme
 *Dağıtımı* , Visual Studio 'Daki bir SharePoint projesinden oluşturulmuş bir SharePoint çözüm dosyasını yerel bir konağa kopyalamaya başvurur. Dağıtılan bir çözümde, Internet Information Services (IIS) havuzunu geri dönüştürme, dağıtımdan sonra çözümü etkinleştirme vb. gibi dağıtım adımlarını yapılandırabilirsiniz. Dağıtmak için, **derleme** menüsündeki **Dağıt** komutunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [nasıl yapılır: bir SharePoint çözümünü yerel bir SharePoint sitesine dağıtma ve yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Yayımlama* , korumalı bir SharePoint çözüm dosyasını uzak bir SharePoint sitesine yüklemeye başvurur; diğer bir deyişle, başka bir sistemde bulunan bir sitedir. Ayrıca, yerel bir SharePoint sitesine bir SharePoint Korumalı çözüm dosyası yayımlayabilirsiniz, ancak yayımlanan sitenin yerel veya uzak olmasına bakılmaksızın dağıtım adımlarını yapılandıramazsınız.

 *Yükseltme* , var olan uzaktan veya yerel olarak yayımlanmış bir SharePoint çözümünü güncelleştirmek anlamına gelir. Visual Studio 'da SharePoint çözümüne herhangi bir değişiklik yapıldıktan sonra çözümün paket dosya adını değiştirirsiniz, çözümü yeniden yayımlayın ve sonra çözümü başarılı bir şekilde yeniden yükledikten sonra çözümü yükseltin. Yerel olarak yayımlanmış bir çözümü yeniden yayımladığınızda, mevcut çözüm dosyasının üzerine yazabilirsiniz.

## <a name="deploy-packages"></a>Paketleri dağıt
 Test ve hata ayıklama için, paket dosyalarını geliştirme bilgisayarınızda SharePoint sunucusuna dağıtabilirsiniz. **Yayımla** Iletişim kutusundaki **dosya sistemine yayınla** seçenek düğmesini seçerek başka bir bilgisayara yükleyebileceğiniz bir paket dosyası da oluşturabilirsiniz. Paket oluşturulup belirtilen yerel dosya yoluna kopyalanır. Bir SharePoint çözümünü yerel sunucuya dağıtmak için, **derleme** menüsündeki **Dağıt** komutunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint çözümünü yerel bir SharePoint sitesine dağıtma ve yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Bir liste tanımını dağıtmayı, bir olay alıcıyı eklemeyi ve özellik tasarımcısını ve paket tasarımcısını kullanmayı öğrenmek için bkz. [Izlenecek yol: proje görev listesi tanımı](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Dağıtım işlemini özelleştirme
 Aşağıdaki tabloda bir SharePoint çözümünü hata ayıkladığınızda ve dağıttığınızda kullanabileceğiniz iki dağıtım yapılandırması gösterilmektedir.

|Dağıtım yapılandırması|Açıklama|
|------------------------------|-----------------|
|Varsayılan|Varsayılan dağıtım yapılandırması. Aşağıdaki dağıtım adımları gerçekleştirilir:<br /><br /> 1. dağıtım öncesi komutunu çalıştırın.<br />2. IIS uygulama havuzunu geri dönüştürün.<br />3. çözümü geri çekin.<br />4. çözüm ekleyin.<br />5. özellikleri etkinleştirin.<br />6. dağıtım sonrası komutunu çalıştırın.<br /><br /> Bir paket kaldırıldığında, aşağıdaki geri çekme adımları gerçekleştirilir.<br /><br /> 1. IIS uygulama havuzunu geri dönüştürün.<br />2. çözümü geri çekin.|
|Etkinleştirme yok|Bu dağıtım yapılandırması, varsayılan yapılandırmayla aynı adımları çalıştırır, ancak Etkinleştirme adımını atlar.|

 Tek bir adımı tamamlayıp dağıtım işlemindeki adımların sırasını değiştirmek için kendi dağıtım yapılandırmalarınızı oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Ayrıca, dağıtımdan önce ve sonra çalıştırılacak komutlar ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Paketleri uzak veya yerel bir sunucuya yayımlayın
 Korumalı bir SharePoint çözümünü uzak bir sunucuya yayımlamak için, menü çubuğunda **Oluştur**, **Yayımla**' yı seçin ve ardından **Yayımla** iletişim kutusunda, uzak sunucunun URL 'sini sağlayan, **SharePoint sitesine yayımla** seçenek düğmesini seçin `https://someremoteserver.sharepoint.microsoftonline.com` .

 Bir SharePoint çözümünü yerel bir sunucuda yayımlamak için, **Yayımla** iletişim kutusunda, yerel sistem yolu sağlayan **dosya sistemine yayınla** seçenek düğmesini seçin.

 Bir çözüm SharePoint 'e başarıyla yayımladıktan sonra çözüm **galerisinde** çözümü etkinleştirebileceğiniz bir yerde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Yayınlanmış paketleri yükselt
 Yayımlandıktan sonra Visual Studio 'da bir SharePoint projesinde değişiklik yaparsanız, yayımlanan paketin değişiklikleri içerecek şekilde yükseltilmesi gerekir. Başarıyla yükseltmek için, bir paketin benzersiz bir adı olmalıdır. SharePoint sitesinde aynı ada sahip bir paket bulunursa, var olan bir uygulamayı güncelleştirirken bu durum, dosya adı çakışmasıyla ilgili bir hata uyarır ve paketi yeniden adlandırmanızı sağlar. Yeniden yayımlandıktan sonra, yeni paket SharePoint sitesinde görünür ve yükseltilebilir. Yükseltilen bir paket, eski paketteki verileri kullanarak çözümü güncelleştirir ve ardından SharePoint 'te çözümü etkinleştirir. Daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
