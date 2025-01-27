---
title: Çözüm paketlerini dağıtma, & ve SharePoint yükseltme
description: Çözüm paketlerini dağıtın, yayımlayın SharePoint yükseltin. Dağıtım işlemini özelleştirme. Paketleri uzak veya yerel bir sunucuda yayımlayın.
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
ms.openlocfilehash: 3101e0f546026f9d030b87238ce7d1630b4ab581
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628214"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Çözüm paketlerini dağıtma, SharePoint ve yükseltme
  Visual Studio'de bir SharePoint çözümü geliştirdikten sonra, paket (.wsp) dosyasını yerel bir SharePoint sunucusuna dağıtabilirsiniz veya uzak veya yerel bir SharePoint sunucuda yayımlayın. Dosyaları dağıtırsanız, paket dosyalarının (.wsp) nasıl dağıtılacağı özelleştirebilirsiniz.

> [!NOTE]
> Şu anda uzak sunucularda yalnızca korumalı SharePoint yayımlanır. Daha fazla bilgi için [bkz. Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

## <a name="deploy-publish-and-upgrade"></a>Dağıtma, yayımlama ve yükseltme
 *Dağıtım,* bir SharePoint projesinde SharePoint bir çözüm Visual Studio yerel bir ana Visual Studio kopyalamayı ifade eder. Dağıtılan bir çözümde, Internet Information Services (IIS) havuzunu geri dönüştürme, dağıtımdan sonra çözümü etkinleştirme gibi dağıtım adımlarını yapılandırabilirsiniz. Dağıtmak için, Derleme **menüsündeki** Dağıt **komutunu** kullanın. Daha fazla bilgi için [bkz.](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) Nasıl SharePoint: SharePoint dağıtım yapılandırmasını düzenleme ve Nasıl: Yerel SharePoint bir SharePoint [sitesinde dağıtma ve yayımlama.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 *Yayımlama,* korumalı alan korumalı bir SharePoint uzak bir siteye SharePoint ifade eder; başka bir sistemde bulunan bir sitedir. Ayrıca, korumalı SharePoint çözüm dosyasını yerel bir SharePoint sitesinde yayımlayın, ancak sitenin yerel mi yoksa uzak mı olduğuna bakılmaksızın dağıtım adımlarını yapılandıramazsanız.

 *Yükseltme, mevcut* bir uzaktan veya yerel olarak yayımlanmış bir çözüm SharePoint ifade eder. SharePoint çözümde herhangi bir değişiklik Visual Studio, çözümün paket dosya adını değiştirir, çözümü yeniden yayımlar ve ardından çözümü başarıyla yeniden yayımlar sonra yükseltebilirsiniz. Yerel olarak yayımlanmış bir çözümü yeniden yayımlarsanız, mevcut çözüm dosyasının üzerine yazabilirsiniz.

## <a name="deploy-packages"></a>Paketleri dağıtma
 Paket dosyalarını test ve hata ayıklama SharePoint geliştirme bilgisayarınızda bir sunucuya dağıtabilirsiniz. Yayımla iletişim kutusundaki Dosya Sistemine Yayımla seçeneğini kullanarak başka bir bilgisayara yük  **devredebilirsiniz.** Paket oluşturulur ve belirtilen yerel dosya yoluna kopyalanır. Yerel sunucuya SharePoint bir çözüm dağıtmak için Derleme **menüsündeki** Dağıt **komutunu** kullanın. Daha fazla bilgi için, [bkz. How to: Deploy and publish a SharePoint to a local SharePoint site](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Bir liste tanımını dağıtma, olay alıcısı ekleme ve Özellik Tasarımcısı ile Paket Tasarımcısı'nın nasıl kullanılası hakkında bilgi edinmek için bkz. Adım adım: Proje [görev listesi tanımını dağıtma.](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)

## <a name="customize-the-deployment-process"></a>Dağıtım işlemini özelleştirme
 Aşağıdaki tabloda, bir çözümde hata ayıklar ve dağıtırken kullanabileceğiniz iki dağıtım SharePoint yer alır.

|Dağıtım yapılandırması|Description|
|------------------------------|-----------------|
|Varsayılan|Varsayılan dağıtım yapılandırması. Aşağıdaki dağıtım adımları gerçekleştirilir:<br /><br /> 1. Dağıtım öncesi komutunu çalıştırın.<br />2. IIS uygulama havuzunu geri dönüştür.<br />3. Çözümü geri çek.<br />4. Çözüm ekleme.<br />5. Özellikleri etkinleştirin.<br />6. Dağıtım sonrası komutunu çalıştırın.<br /><br /> Bir paket kaldırılana kadar aşağıdaki geri çekme adımları gerçekleştirilir.<br /><br /> 1. IIS uygulama havuzunu geri dönüştür.<br />2. Çözümü geri çek.|
|Etkinleştirme yok|Bu dağıtım yapılandırması, Varsayılan yapılandırma ile aynı adımları çalıştırır, ancak etkinleştirme adımını atlar.|

 Tek bir adımı tamamlamak veya dağıtım işlemi adımlarının sıralamalarını değiştirmek için kendi dağıtım yapılandırmalarınızı oluşturabilirsiniz. Daha fazla bilgi için, [bkz. How to: Edit a SharePoint deployment configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Dağıtımdan önce ve sonra çalıştıracak komutlar da ekebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Dağıtım komutlarını SharePoint ayarlama.](../sharepoint/how-to-set-sharepoint-deployment-commands.md)

## <a name="publish-packages-to-a-remote-or-local-server"></a>Paketleri uzak veya yerel bir sunucuya yayımlama
 Korumalı bir SharePoint çözümünü uzak bir sunucuya yayımlamak için, menü çubuğunda, Derleme **,**  Yayımla 'yı seçin ve ardından Yayımla iletişim kutusunda, uzak sunucunun URL'sini sağlayarak , gibi uzak sunucunun URL'sini sağlayarak **Yayımla iletişim** kutusunda SharePoint Sitesinde Yayımla seçeneğini `https://someremoteserver.sharepoint.microsoftonline.com` belirleyin.

 Bir SharePoint çözümü yerel bir sunucuya yayımlamak  için, Yayımla  iletişim kutusunda Dosya Sisteminde Yayımla seçeneğini belirleyin ve yerel bir sistem yolu belirtin.

 Bir çözüm başarıyla SharePoint çözüm Çözüm **Galerisi'nde görüntülenir ve** burada çözümü etkinleştirebilirsiniz. Daha fazla bilgi için, [bkz. How to: Deploy, publish, and upgrade SharePoint on a remote server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Yayımlanan paketleri yükseltme
 Bir proje yayımlandıktan sonra SharePoint projesinde Visual Studio değişiklikleri eklemek için yayımlanmış paketin yükseltilmesi gerekir. Başarıyla yükseltmek için paketin benzersiz bir adı olmalıdır. SharePoint sitesinde aynı adı içeren bir paket bulunursa (mevcut bir uygulamayı güncelleştiriyorsanız) hata sizi dosya adı çakışması için uyarır ve paketi yeniden adlandırmanızı sağlar. Yeniden yayımlanmayan yeni paket, SharePoint yükseltilebilir. Yükseltilmiş bir paket, eski paketten verileri kullanarak çözümü güncelleştirmenin ardından çözümü SharePoint. Daha fazla bilgi için, [bkz. How to: Deploy, publish, and upgrade SharePoint on a remote server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çözümlerini paket SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
