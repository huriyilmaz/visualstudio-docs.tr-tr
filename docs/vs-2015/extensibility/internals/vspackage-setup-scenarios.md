---
title: VSPackage kurulum senaryoları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696751"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir esneklik için VSPackage yükleyicinizi tasarlamak önemlidir. Örneğin, gelecekte bir güvenlik düzeltme ekini serbest bırakmanız veya kapsamlı yan yana sürüm desteği gerektiren bir iş stratejisini değiştirmeniz gerekebilir.  
  
 [Visual Studio 'Nun birden çok sürümünü destekleyerek](../../extensibility/supporting-multiple-versions-of-visual-studio.md), [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage 'ın paylaşılan veya yan yana yüklemeleri ile yan yana yüklemelerini destekleme avantajları ve sorunları hakkında bilgi edinebilirsiniz. Kısa bir yandan yan yana VSPackages, ' nin yeni özelliklerini desteklemek için size en fazla esneklik sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Bu konuda tartışılan senaryolar yalnızca Seçimlerinizden değildir, ancak önerilen en iyi uygulamalar olarak sunulur.  
  
## <a name="components-privacy-and-sharing"></a>Bileşenler, gizlilik ve paylaşım  
  
##### <a name="make-your-components-independent"></a>Bileşenlerinizi bağımsız hale getirme  
 Bir bileşeni tanımladıktan ve doldurduktan, bir bileşeni atadıktan `GUID` ve dağıttıktan sonra, kompozisyonunu değiştiremezsiniz. Bir bileşenin kompozisyonunu değiştirirseniz, sonuçta elde edilen bileşen yeni bir bileşen olmalıdır `GUID` . Bu olgular verildiğinde, en büyük sürüm oluşturma esnekliği, her bileşene bağımsız, kendine bağlı birim yapılarak gerçekleştirilir. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için bkz. [bileşen kodunu değiştirme](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) ve [bileşen kuralları bozulur ne olur?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx).  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Bir bileşende paylaşılan ve özel kaynakları karıştırma  
 Başvuru sayımı bileşen düzeyinde oluşur. Sonuç olarak, paylaşılan ve özel kaynakları tek bir bileşende karıştırmak, paylaşılan kaynakların üzerine yazmadan yürütülebilir bir dosya gibi özel kaynakların güncelleştirilmesini olanaksız hale getirir. Bu senaryo, geriye dönük uyumluluk sorunları oluşturur ve yan yana yetenek oluşturma işlemini kısıtlar.  
  
 Örneğin, ile VSPackage 'ı kaydetmek için kullanılan kayıt defteri değerleri, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] VSPackage 'ı ile kaydetmek için kullanılan bir bileşende ayrı bir bileşende tutulmalıdır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Paylaşılan dosyalar veya kayıt defteri değerleri, başka bir bileşeni de daha sonra gider.  
  
## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage  
 Bu senaryoda, bir Paylaşılan VSPackage (birden çok sürümünü destekleyen tek bir ikili [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) Windows Installer bir pakette gönderilir. Her sürümüyle kaydolmak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , Kullanıcı tarafından seçilebilen Özellikler tarafından denetlenir. Ayrıca, ayrı özelliklere atandığında her bir bileşen yükleme veya kaldırma için tek tek seçilebileceği anlamına gelir ve kullanıcıyı VSPackage 'ın farklı sürümlerine tümleştirme denetimine koymaktır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . (Windows Installer paketlerindeki özellikleri kullanma hakkında daha fazla bilgi için bkz. [Windows Installer özellikleri](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) .)  
  
 ![VS Paylaşılan VSPackage grafiği](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
Paylaşılan VSPackage yükleyicisi  
  
 Çizimde gösterildiği gibi, paylaşılan bileşenler her zaman yüklenen Feat_Common özelliğinin bir parçası haline getirilir. Feat_VS2002 ve Feat_VS2003 özelliklerinin görünür hale getirilmesi, kullanıcılar, VSPackage 'ın hangi sürümlerinin tümleştirileceğini istedikleri, yüklemesi sırasında seçebilirler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Kullanıcılar ayrıca, özellik eklemek veya kaldırmak için Windows Installer bakım modunu da kullanabilir. Bu durumda, bu örnekte farklı sürümlerindeki VSPackage kayıt bilgilerini ekler veya kaldırır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Özelliğin görüntüleme sütununun 0 olarak ayarlanması onu gizler. 1 gibi düşük düzey bir sütun değeri, her zaman yüklenmesini sağlar. Daha fazla bilgi için bkz. [INSTALLLEVEL özelliği](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) ve [özellik tablosu](https://msdn.microsoft.com/library/aa368585.aspx).  
  
## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage güncelleştirmesi  
 Bu senaryoda, senaryo 1 ' de VSPackage yükleyicisinin güncelleştirilmiş bir sürümü gönderilir. Tartışma açısından, güncelleştirme için destek ekler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ancak daha basit bir güvenlik düzeltme eki veya hata düzeltme hizmet paketi de olabilir. Windows Installer daha yeni bileşenleri yükleme kuralları, sistemde zaten değiştirilmemiş bileşenlerin yeniden kopyalanmadığını gerektirir. Bu durumda, 1,0 sürümünü içeren bir sistem, güncelleştirilmiş bileşen Comp_MyVSPackage.dll üzerine yazar ve kullanıcıların bileşen Comp_VS2005_Reg yeni özellik Feat_VS2005 eklemeyi seçmesini sağlar.  
  
> [!CAUTION]
> Birden çok sürümü arasında bir VSPackage paylaşıldığında [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , VSPackage sonraki sürümlerinin önceki sürümleriyle geriye dönük uyumluluk sağlamak önemlidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Geriye dönük uyumluluğu koruyabileceğiniz yerlerde yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Nun birden çok sürümünü destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
 ![VS Paylaşılan VS paketi güncelleştirme resmi](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
Paylaşılan VSPackage güncelleştirme yükleyicisi  
  
 Bu senaryo, küçük yükseltme desteğinin Windows Installer avantajlarından yararlanarak yeni bir VSPackage yükleyicisi sunmaktadır. Kullanıcılar yalnızca sürüm 1,1 ' ü yükler ve BT sürüm 1,0 ' i yükseltir. Ancak sistemde sürüm 1,0 ' ün olması gerekmez. Aynı Yükleyici sürüm 1,1 ' i sürüm 1,0 olmadan bir sisteme yükler. Bu şekilde küçük yükseltmeler sağlamanın avantajı, bir yükseltme yükleyicisi geliştirme ve tam ürün yükleyicisi geliştirme çalışmalarından faydalanmak için gerekli değildir. Bir yükleyici her iki işi de yapar. Bunun yerine bir güvenlik düzeltme veya hizmet paketi Windows Installer düzeltme eklerinden faydalanabilir. Daha fazla bilgi için bkz. [düzeltme eki uygulama ve yükseltme](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx).  
  
## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: yan yana VSPackage  
 Bu senaryo, Visual Studio .NET 2003 ve ' nin her sürümü için bir tane olmak üzere iki VSPackage yükleyicisi sunar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Her yükleyici, yan yana veya özel bir VSPackage (özellikle belirli bir sürümü için oluşturulmuş ve yüklenmiş bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ) yüklenir. Her VSPackage kendi bileşenidir. Sonuç olarak, her biri düzeltme ekleri veya bakım yayımları ile tek tek hizmet verebilir. VSPackage DLL 'SI artık sürüme özgü olduğundan, kayıt bilgilerini DLL ile aynı bileşene eklemek güvenlidir.  
  
 ![&#45;tarafı VS Paketi grafiğine göre VS tarafı&#45;](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Yan yana VSPackage yükleyicisi  
  
 Her yükleyici Ayrıca iki yükleyici arasında paylaşılan kod içerir. Paylaşılan kod ortak bir konuma yüklenirse, hem. msi dosyalarını yüklemek paylaşılan kodu yalnızca bir kez yükler. İkinci yükleyici, bileşen üzerindeki bir başvuru sayısını artırır. Başvuru sayısı, VSPackages 'tan birinin kaldırılması durumunda, paylaşılan kodun diğer VSPackage için de kalacağını sağlar. İkinci VSPackage da kaldırılırsa, paylaşılan kod kaldırılır.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: yan yana VSPackage güncelleştirmesi  
 Bu senaryoda, VSPackage, [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] bir güvenlik güvenlik açığıyla karşılaştı ve bir güncelleştirme yapmanız gerekiyor. Senaryo 2 ' de olduğu gibi, güvenlik düzeltmesini dahil etmek için mevcut bir yüklemeyi güncelleştiren ve güvenlik düzeltmesinin zaten bulunduğu yeni yüklemeleri dağıtan yeni bir. msi dosyası oluşturabilirsiniz.  
  
 Bu durumda, VSPackage, genel derleme önbelleğinde (GAC) yüklü bir yönetilen VSPackage ' dır. Güvenlik düzeltmesini dahil etmek için onu yeniden oluşturduğunuzda, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Yeni derleme sürüm numarası için kayıt bilgileri önceki sürümün üzerine yazılır ve bu da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sabit derlemeyi yüklemeye neden olur.  
  
 ![&#45;tarafı VS paketi güncelleştirme grafiğine göre VS tarafındaki&#45;](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Yan yana VSPackage güncelleştirme yükleyicisi  
  
 **Göz önünde** Yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için bkz. [.NET Framework dağıtım ve çözme dll Hell](https://msdn.microsoft.com/library/ms973843.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
