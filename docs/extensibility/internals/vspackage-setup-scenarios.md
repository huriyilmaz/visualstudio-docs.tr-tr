---
title: VSPackage kurulum senaryoları | Microsoft Docs
description: vspackage 'ın paylaşılan veya yan yana yüklemeleri ile Visual Studio yan yana yüklemelerini desteklemeye yönelik en iyi yöntemler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e75851e8a2775fda80a4bcb6ffefa93558c4f786
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724994"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları

Bir esneklik için VSPackage yükleyicinizi tasarlamak önemlidir. Örneğin, gelecekte bir güvenlik düzeltme ekini serbest bırakmanız veya kapsamlı yan yana sürüm desteği gerektiren bir iş stratejisini değiştirmeniz gerekebilir.

[Visual Studio birden çok sürümünü destekleyerek](../../extensibility/supporting-multiple-versions-of-visual-studio.md), [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vspackage 'ın paylaşılan veya yan yana yüklemeleri ile yan yana yüklemelerini destekleme avantajları ve sorunları hakkında bilgi edinebilirsiniz. Kısa bir yandan yan yana VSPackages, ' nin yeni özelliklerini desteklemek için size en fazla esneklik sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Bu konuda tartışılan senaryolar yalnızca Seçimlerinizden değildir, ancak önerilen en iyi uygulamalar olarak sunulur.

## <a name="components-privacy-and-sharing"></a>Bileşenler, gizlilik ve paylaşım

### <a name="make-your-components-independent"></a>Bileşenlerinizi bağımsız hale getirme

Bir bileşeni tanımladıktan ve doldurduktan, bir bileşeni atadıktan `GUID` ve dağıttıktan sonra, kompozisyonunu değiştiremezsiniz. Bir bileşenin kompozisyonunu değiştirirseniz, sonuçta elde edilen bileşen yeni bir bileşen olmalıdır `GUID` . Bu olgular verildiğinde, en büyük sürüm oluşturma esnekliği, her bileşene bağımsız, kendine bağlı birim yapılarak gerçekleştirilir. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için bkz. [bileşen kodunu değiştirme](/windows/desktop/Msi/changing-the-component-code) ve [bileşen kuralları bozulur ne olur?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Bir bileşende paylaşılan ve özel kaynakları karıştırma

Başvuru sayımı bileşen düzeyinde oluşur. Sonuç olarak, paylaşılan ve özel kaynakları tek bir bileşende karıştırmak, paylaşılan kaynakların üzerine yazmadan yürütülebilir bir dosya gibi özel kaynakların güncelleştirilmesini olanaksız hale getirir. Bu senaryo, geriye dönük uyumluluk sorunları oluşturur ve yan yana yetenek oluşturma işlemini kısıtlar.

Örneğin, VSPackage 'ı kaydetmek için kullanılan kayıt defteri değerleri, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] VSPackage 'ı Visual Studio kaydetmek için kullanılan bir bileşende ayrı bir bileşende tutulmalıdır. Paylaşılan dosyalar veya kayıt defteri değerleri, başka bir bileşeni de daha sonra gider.

## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage

bu senaryoda, paylaşılan bir vspackage (Visual Studio birden çok sürümünü destekleyen tek bir ikili dosya Windows Installer paketine gönderilir. her bir Visual Studio sürümüne kaydolmak, kullanıcı tarafından seçilebilen özelliklerle denetlenir. Ayrıca, ayrı özelliklere atandığında her bir bileşen yükleme veya kaldırma için tek tek seçilebileceği anlamına gelir ve kullanıcıyı VSPackage 'ın farklı sürümlerine tümleştirme denetimine koymaktır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . (Windows Installer paketlerindeki özellikleri kullanma hakkında daha fazla bilgi için bkz. [Windows Installer özellikleri](/windows/desktop/Msi/windows-installer-features) .)

![VS Paylaşılan VSPackage yükleyicisi](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Çizimde gösterildiği gibi, paylaşılan bileşenler her zaman yüklenen Feat_Common özelliğinin bir parçası haline getirilir. Feat_VS2002 ve Feat_VS2003 özelliklerinin görünür hale getirilmesi, kullanıcılar, vspackage 'un tümleştirileceği Visual Studio sürümlerinin bir yüklemesini tercih edebilir. kullanıcılar ayrıca, özellik eklemek veya kaldırmak için Windows Installer bakım modunu da kullanabilir. bu durumda, Visual Studio farklı sürümlerindeki vspackage kayıt bilgilerini ekler veya kaldırır.

> [!NOTE]
> Özelliğin görüntüleme sütununun 0 olarak ayarlanması onu gizler. 1 gibi düşük düzey bir sütun değeri, her zaman yüklenmesini sağlar. Daha fazla bilgi için bkz. [INSTALLLEVEL özelliği](/windows/desktop/Msi/installlevel) ve [özellik tablosu](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage güncelleştirmesi

Bu senaryoda, senaryo 1 ' de VSPackage yükleyicisinin güncelleştirilmiş bir sürümü gönderilir. tartışma için, güncelleştirme Visual Studio için destek ekler, ancak daha basit bir güvenlik düzeltme eki veya hata düzeltme hizmet paketi de olabilir. Windows Yükleyicinin daha yeni bileşenleri yükleme kuralları, sistemde zaten değiştirilmemiş bileşenlerin yeniden kopyalanmaması gerekir. Bu durumda, 1,0 sürümünü içeren bir sistem, güncelleştirilmiş bileşen Comp_MyVSPackage.dll üzerine yazar ve kullanıcıların bileşen Comp_VS2005_Reg yeni özellik Feat_VS2005 eklemeyi seçmesini sağlar.

> [!CAUTION]
> Birden çok sürümü arasında bir VSPackage paylaşıldığında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , VSPackage 'un sonraki sürümlerinde Visual Studio önceki sürümleriyle geriye dönük uyumluluk sağlamak önemlidir. Geriye dönük uyumluluğu koruyabileceğiniz yerlerde yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio birden çok sürümünü destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS Paylaşılan VS paketi güncelleştirme yükleyicisi](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

bu senaryo, küçük yükseltme desteğinin Windows Installer avantajlarından yararlanarak yeni bir vspackage yükleyicisi sunmaktadır. Kullanıcılar yalnızca sürüm 1,1 ' ü yükler ve BT sürüm 1,0 ' i yükseltir. Ancak sistemde sürüm 1,0 ' ün olması gerekmez. Aynı Yükleyici sürüm 1,1 ' i sürüm 1,0 olmadan bir sisteme yükler. Bu şekilde küçük yükseltmeler sağlamanın avantajı, bir yükseltme yükleyicisi geliştirme ve tam ürün yükleyicisi geliştirme çalışmalarından faydalanmak için gerekli değildir. Bir yükleyici her iki işi de yapar. bunun yerine bir güvenlik düzeltme veya hizmet paketi Windows Installer düzeltme eklerinden faydalanabilir. Daha fazla bilgi için bkz. [düzeltme eki uygulama ve yükseltme](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: yan yana VSPackage

bu senaryoda, .net 2003 ve Visual Studio Visual Studio her sürümü için bir tane olmak üzere iki vspackage yükleyicisi sunulmaktadır. Her yükleyici, bir yan yana veya özel, VSPackage (belirli bir Visual Studio sürümü için özel olarak oluşturulan ve yüklenen) yüklenir. Her VSPackage kendi bileşenidir. Sonuç olarak, her biri düzeltme ekleri veya bakım yayımları ile tek tek hizmet verebilir. VSPackage DLL 'SI artık sürüme özgü olduğundan, kayıt bilgilerini DLL ile aynı bileşene eklemek güvenlidir.

![VS yan yana VS paketi yükleyicisi](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Her yükleyici Ayrıca iki yükleyici arasında paylaşılan kod içerir. Paylaşılan kod ortak bir konuma yüklenirse, her iki .msi dosyasını yüklemek paylaşılan kodu yalnızca bir kez yükler. İkinci yükleyici, bileşen üzerindeki bir başvuru sayısını artırır. Başvuru sayısı, VSPackages 'tan birinin kaldırılması durumunda, paylaşılan kodun diğer VSPackage için de kalacağını sağlar. İkinci VSPackage da kaldırılırsa, paylaşılan kod kaldırılır.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: yan yana VSPackage güncelleştirmesi

bu senaryoda, Visual Studio için vspackage bir güvenlik güvenlik açığıyla karşılaştı ve bir güncelleştirme yapmanız gerekiyor. Senaryo 2 ' de olduğu gibi, var olan bir yüklemeyi güvenlik düzeltmesini içerecek şekilde güncelleştiren yeni bir .msi dosyası oluşturabilir ve güvenlik düzeltmesinin zaten bulunduğu yeni yüklemeleri dağıtabilirsiniz.

Bu durumda, VSPackage, genel derleme önbelleğinde (GAC) yüklü bir yönetilen VSPackage ' dır. Güvenlik düzeltmesini dahil etmek için onu yeniden oluşturduğunuzda, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Yeni derleme sürüm numarası için kayıt bilgileri önceki sürümün üzerine yazılır ve bu da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sabit derlemeyi yüklemeye neden olur.

![VS yan yana VS paketi güncelleştirme yükleyicisi](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için bkz. [.NET Framework dağıtım ve çözme dll Hell](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)