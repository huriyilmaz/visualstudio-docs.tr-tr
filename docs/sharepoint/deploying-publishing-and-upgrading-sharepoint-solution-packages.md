---
title: '& SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme'
description: SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme. Dağıtım işlemini özelleştirin. Paketleri uzak veya yerel bir sunucuya yayımlayın.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d0dd6332a6ce1f7b0a1940e392918004f246cc525ab48030c15085b82ba54d42
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425537"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme
  Visual Studio bir SharePoint çözümü geliştirdikten sonra, paket (. wsp) dosyasını yerel bir SharePoint sunucusuna dağıtabilir veya uzak ya da yerel bir SharePoint sunucusuna yayımlayabilirsiniz. Dosyaları dağıtırsanız, paket dosyalarının (. wsp) nasıl dağıtıldığını özelleştirebilirsiniz.

> [!NOTE]
> şu anda, uzak SharePoint sunucularında yalnızca korumalı çözümler yayımlanabilir. Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Dağıtma, yayımlama ve yükseltme
 *dağıtımı* , Visual Studio bir SharePoint projesinden oluşturulan SharePoint çözüm dosyasını yerel bir konağa kopyalamaya başvurur. dağıtılan bir çözümde, Internet Information Services (ııs) havuzunu geri dönüştürme, dağıtımdan sonra çözümü etkinleştirme vb. gibi dağıtım adımlarını yapılandırabilirsiniz. Dağıtmak için, **derleme** menüsündeki **Dağıt** komutunu kullanın. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [nasıl yapılır: yerel bir SharePoint sitesine bir SharePoint çözümü dağıtma ve yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *yayımlama* , korumalı bir SharePoint çözüm dosyasını uzak bir SharePoint sitesine yüklemeyi ifade eder; diğer bir deyişle, başka bir sistemde bulunan bir sitedir. ayrıca, bir SharePoint korumalı çözüm dosyasını yerel bir SharePoint sitesine yayımlayabilirsiniz, ancak yayımlanan sitenin yerel veya uzak olmasına bakılmaksızın dağıtım adımlarını yapılandıramazsınız.

 *yükseltme* , var olan uzaktan veya yerel olarak yayımlanmış SharePoint çözümünü güncelleştirmek anlamına gelir. Visual Studio SharePoint çözümüne yapılan herhangi bir değişiklik yapıldıktan sonra çözümün paket dosya adını değiştirirsiniz, çözümü yeniden yayımlayın ve sonra çözümü başarılı bir şekilde yeniden yükledikten sonra yükseltebilirsiniz. Yerel olarak yayımlanmış bir çözümü yeniden yayımladığınızda, mevcut çözüm dosyasının üzerine yazabilirsiniz.

## <a name="deploy-packages"></a>Paketleri dağıt
 test ve hata ayıklama için, paket dosyalarını geliştirme bilgisayarınızda SharePoint sunucusuna dağıtabilirsiniz. **Yayımla** Iletişim kutusundaki **dosya sistemine yayınla** seçenek düğmesini seçerek başka bir bilgisayara yükleyebileceğiniz bir paket dosyası da oluşturabilirsiniz. Paket oluşturulup belirtilen yerel dosya yoluna kopyalanır. yerel sunucuya bir SharePoint çözümü dağıtmak için, **derleme** menüsündeki **dağıt** komutunu kullanın. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümünü dağıtma ve yerel SharePoint sitesine yayımlama](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Bir liste tanımını dağıtmayı, bir olay alıcıyı eklemeyi ve özellik tasarımcısını ve paket tasarımcısını kullanmayı öğrenmek için bkz. [Izlenecek yol: proje görev listesi tanımı](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Dağıtım işlemini özelleştirme
 aşağıdaki tabloda, bir SharePoint çözümü hata ayıklarken ve dağıtırken kullanabileceğiniz iki dağıtım yapılandırması gösterilmektedir.

|Dağıtım yapılandırması|Açıklama|
|------------------------------|-----------------|
|Varsayılan|Varsayılan dağıtım yapılandırması. Aşağıdaki dağıtım adımları gerçekleştirilir:<br /><br /> 1. dağıtım öncesi komutunu çalıştırın.<br />2. IIS uygulama havuzunu geri dönüştürün.<br />3. çözümü geri çekin.<br />4. çözüm ekleyin.<br />5. özellikleri etkinleştirin.<br />6. dağıtım sonrası komutunu çalıştırın.<br /><br /> Bir paket kaldırıldığında, aşağıdaki geri çekme adımları gerçekleştirilir.<br /><br /> 1. IIS uygulama havuzunu geri dönüştürün.<br />2. çözümü geri çekin.|
|Etkinleştirme yok|Bu dağıtım yapılandırması, varsayılan yapılandırmayla aynı adımları çalıştırır, ancak Etkinleştirme adımını atlar.|

 Tek bir adımı tamamlayıp dağıtım işlemindeki adımların sırasını değiştirmek için kendi dağıtım yapılandırmalarınızı oluşturabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Ayrıca, dağıtımdan önce ve sonra çalıştırılacak komutlar ekleyebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım komutlarını ayarlama](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Paketleri uzak veya yerel bir sunucuya yayımlayın
 korumalı bir SharePoint çözümünü uzak bir sunucuya yayımlamak için, menü çubuğunda **oluştur**, **yayımla**' yı seçin ve ardından **yayımla** iletişim kutusunda, uzak sunucunun URL 'sini sağlayan **SharePoint sitede yayımla** seçenek düğmesini seçin `https://someremoteserver.sharepoint.microsoftonline.com` .

 bir SharePoint çözümünü yerel bir sunucuya yayımlamak için, **yayımla** iletişim kutusunda, yerel sistem yolu sağlayan **dosya sistemine yayınla** seçenek düğmesini seçin.

 bir çözüm SharePoint başarılı bir şekilde yayımlandıktan sonra çözüm **galerisinde** , çözümü etkinleştirebileceğiniz şekilde görünür. daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Yayınlanmış paketleri yükselt
 yayımlandıktan sonra Visual Studio SharePoint projede herhangi bir değişiklik yaparsanız, yayımlanan paketin değişiklikleri içerecek şekilde yükseltilmesi gerekir. Başarıyla yükseltmek için, bir paketin benzersiz bir adı olmalıdır. SharePoint sitede aynı ada sahip bir paket bulunursa, var olan bir uygulamayı güncelleştirirken oluşabilecek bir hata, dosya adı çakışmasıyla ilgili olarak sizi uyarır ve paketi yeniden adlandırmanızı sağlar. yeniden yayımlandıktan sonra, yeni paket SharePoint sitesinde görüntülenir ve yükseltilecektir. Yükseltilen bir paket, eski paketteki verileri kullanarak çözümü güncelleştirir ve sonra SharePoint çözüm etkinleştirir. daha fazla bilgi için bkz. [nasıl yapılır: uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
