---
title: SharePoint çözüm paketlerini dağıtma, yayımlama & yükseltme
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
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444976"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme
  Visual Studio'da bir SharePoint çözümü geliştirdikten sonra, paket (.wsp) dosyasını yerel bir SharePoint sunucusuna dağıtabilir veya uzak veya yerel bir SharePoint sunucusunda yayımlayabilirsiniz. Dosyaları dağıtırsanız, paket dosyalarının (.wsp) nasıl dağıtılandığını özelleştirebilirsiniz.

> [!NOTE]
> Şu anda, yalnızca kumlu çözümler uzak SharePoint sunucularına yayınlanabilir. Daha fazla bilgi için Bkz. [Sandboxed çözüm konuları.](../sharepoint/sandboxed-solution-considerations.md)

## <a name="deploy-publish-and-upgrade"></a>Dağıtma, yayımlama ve yükseltme
 *Dağıtım,* Visual Studio'daki bir SharePoint projesinden yerel bir ana bilgisayara oluşturulmuş bir SharePoint çözüm dosyasını kopyalama anlamına gelir. Dağıtılan bir çözümde, Internet Bilgi Hizmetleri (IIS) havuzunu geri dönüştürme, dağıtımdan sonra çözümü etkinleştirme vb. dağıtım adımlarını yapılandırabilirsiniz. Dağıtmak için **Yapı** menüsündeki **Dağıt** komutunu kullanın. Daha fazla bilgi için [bkz: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) ve [Nasıl Yapılacağı: Bir SharePoint çözümlerini Yerel SharePoint sitesine dağıtma ve yayımlama.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 *Yayımlama,* uzak bir SharePoint sitesine kumhavuzuyla sharepoint çözüm dosyası yüklemek anlamına gelir; başka bir sistem üzerinde bulunan bir site. SharePoint sandboxed çözüm dosyasını yerel bir SharePoint sitesine de yayımlayabilirsiniz, ancak yayınlanan sitenin yerel veya uzak olup olmadığına bakılmaksızın dağıtım adımlarını yapılandıramazsınız.

 *Yükseltme,* varolan uzaktan veya yerel olarak yayınlanan bir SharePoint çözümlerini güncelleştirmeyi ifade eder. Visual Studio'daki SharePoint çözümünde herhangi bir değişiklik yapıldıktan sonra, çözümün paket dosya adını değiştirir, çözümü yeniden yayımlar ve çözümü başarıyla yeniden yayımladıktan sonra yükseltirsiniz. Yerel olarak yayımlanan bir çözümü yeniden yayımlarsanız, varolan çözüm dosyasının üzerine yazabilirsiniz.

## <a name="deploy-packages"></a>Paketleri dağıtma
 Paket dosyalarını geliştirme bilgisayarınızdaki SharePoint sunucusuna sınama ve hata ayıklama için dağıtabilirsiniz. Ayrıca, **Dosya** Sistemi Için Yayımla iletişim kutusundaki Dosya Sistemi Için **Yayımla** seçeneğini seçerek başka bir bilgisayara yükleyebileceğiniz bir paket dosyası da oluşturabilirsiniz. Paket oluşturulur ve belirtilen yerel dosya yoluna kopyalanır. Yerel sunucuya bir SharePoint çözümdağıtmak için **Yapı** menüsündeki **Dağıt** komutunu kullanın. Daha fazla bilgi için [bkz: Nasıl dağıtılır ve yerel bir SharePoint sitesine SharePoint çözümlerini dağıtın ve yayımlayın.](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)

 Liste tanımını nasıl dağıtılayabilirsiniz, olay alıcısı eklemeyi ve Özellik Tasarımcısı ve Paket Tasarımcısı'nı kullanmayı öğrenmek için [Bkz. Walkthrough: Proje görev listesi tanımını dağıtın.](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)

## <a name="customize-the-deployment-process"></a>Dağıtım işlemini özelleştirme
 Aşağıdaki tablo, bir SharePoint çözümlerini hata ayıklarken ve dağıtırken kullanabileceğiniz iki dağıtım yapılandırmasını gösterir.

|Dağıtım yapılandırması|Açıklama|
|------------------------------|-----------------|
|Varsayılan|Varsayılan dağıtım yapılandırması. Aşağıdaki dağıtım adımları gerçekleştirilir:<br /><br /> 1. Ön dağıtım komutunu çalıştırın.<br />2. IIS uygulama havuzugeri dönüşüm.<br />3. Çözeltiyi geri çekin.<br />4. Çözüm ekleyin.<br />5. Özellikleri etkinleştirin.<br />6. Dağıtım sonrası komutu çalıştırın.<br /><br /> Bir paket kaldırıldığında, aşağıdaki geri çekme adımları gerçekleştirilir.<br /><br /> 1. IIS uygulama havuzugeri dönüşüm.<br />2. Çözeltiyi geri çekin.|
|Etkinleştirme yok|Bu dağıtım yapılandırması Varsayılan yapılandırmayla aynı adımları çalıştırır, ancak etkinleştirme adımını atlar.|

 Tek bir adımı tamamlamak veya dağıtım işlemindeki adımların sırasını değiştirmek için kendi dağıtım yapılandırmalarınızı oluşturabilirsiniz. Daha fazla bilgi için [bkz: SharePoint dağıtım yapılandırmasını düzenleme.](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)

 Dağıtımdan önce ve sonra çalıştırmak için komutlar da ekleyebilirsiniz. Daha fazla bilgi için [bkz: SharePoint dağıtım komutlarını ayarlayın.](../sharepoint/how-to-set-sharepoint-deployment-commands.md)

## <a name="publish-packages-to-a-remote-or-local-server"></a>Paketleri uzak veya yerel bir sunucuda yayımlama
 Uzak bir sunucuya, menü çubuğunda sandboxed SharePoint çözümlerini yayımlamak **için, Yap**, **Yayımla**ve ardından **Yayımla** iletişim kutusunda, uzak sunucunun URL'sini sağlayan **SharePoint Site** seçeneğine yayımla seçeneğini `https://someremoteserver.sharepoint.microsoftonline.com`belirleyin.

 Bir SharePoint çözümlerini yerel bir sunucuya yayımlamak için, **Yayımla** iletişim kutusunda, yerel bir sistem yolu sağlayan Dosya Sistemi için **Yayımla** seçeneğini seçin.

 Bir çözüm SharePoint'te başarıyla yayımladıktan sonra, çözüm etkinleştirebileceğiniz **Çözüm Galerisi'nde** görünür. Daha fazla bilgi için [bkz: Uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

### <a name="upgrade-published-packages"></a>Yayımlanmış paketleri yükseltme
 Visual Studio'daki bir SharePoint projesinde yayımlandıktan sonra herhangi bir değişiklik yaparsanız, yayınlanan paket değişiklikleri içerecek şekilde yükseltilmelidir. Başarılı bir şekilde yükseltmek için bir paketin benzersiz bir adı olması gerekir. SharePoint sitesinde aynı ada sahip bir paket bulunursa - ki varolan bir uygulamayı güncelleştirdiğinizde oluşabilir - bir hata sizi dosya adı çakışması konusunda uyarır ve paketi yeniden adlandırmanıza olanak tanır. Yeniden yayımlandıktan sonra, yeni paket SharePoint sitesinde görünür ve yükseltilebilir. Yükseltilmiş bir paket, eski paketteki verileri kullanarak çözümü güncelleştirir ve çözümü SharePoint'te etkinleştirir. Daha fazla bilgi için [bkz: Uzak bir sunucuda SharePoint çözümlerini dağıtma, yayımlama ve yükseltme.](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleyip dağıtın](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
