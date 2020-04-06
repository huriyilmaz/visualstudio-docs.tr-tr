---
title: VSPackage Kurulum Senaryoları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703981"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage Kurulum Senaryoları

Esneklik için VSPackage yükleyicinizi tasarlamak önemlidir. Örneğin, gelecekte bir güvenlik yamayayımlamanız gerekebilir veya kapsamlı yan yana sürüm desteği gerektiren bir iş stratejisini değiştirebilirsiniz.

[Visual Studio'nun Birden Çok Sürümlerini Desteklerken,](../../extensibility/supporting-multiple-versions-of-visual-studio.md)VSPackage'ınızın paylaşılan veya yan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yana kurulumlarının yan yana kurulumlarını desteklemenin avantajları ve sorunları hakkında bilgi edinebilirsiniz. Kısacası, yan yana VSPackages yeni özellikleri desteklemek için en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fazla esneklik sağlar.

Bu konuda tartışılan senaryolar yalnızca seçenekleriniz değildir, ancak önerilen en iyi uygulamalar olarak sunulur.

## <a name="components-privacy-and-sharing"></a>Bileşenler, Gizlilik ve Paylaşım

### <a name="make-your-components-independent"></a>Bileşenlerinizi bağımsız hale getirin

Bir bileşeni tanımladıktan ve doldurduktan, bir `GUID`bileşen atadıktan ve dağıttıktan sonra, bileşeni değiştiremezsiniz. Bir bileşenin bileşimini değiştirirseniz, elde edilen bileşen yeni `GUID`bir bileşene sahip yeni bir bileşen olmalıdır. Bu gerçekler göz önüne alındığında, en büyük sürüm esnekliği her bileşeni bağımsız, kendine güvenen birim yaparak karşılanır. Bileşenleri yöneten kurallar hakkında daha fazla bilgi için [What Happens if the Component Rules Are Broken?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken) [bkz.](/windows/desktop/Msi/changing-the-component-code)

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Paylaşılan ve özel kaynakları bir bileşende karıştırmayın

Başvuru sayımı bileşen düzeyinde gerçekleşir. Sonuç olarak, paylaşılan ve özel kaynakları tek bir bileşende karıştırmak, paylaşılan kaynakların üzerine yazmadan yürütülebilir bir dosya gibi özel kaynakların güncelleştirilen şekilde güncelleştirilen bir şekilde güncelleştirileni imkansız hale getirir. Bu senaryo geriye dönük uyumluluk sorunları oluşturur ve yan yana yeteneği oluşturmanızı kısıtlar.

Örneğin, VSPackage'ınızı kaydetmek için kullanılan [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kayıt defteri değerleri, VSPackage'ınızı Visual Studio'ya kaydettirmek için kullanılan bileşenden ayrı bir bileşende tutulmalıdır. Paylaşılan dosyalar veya kayıt defteri değerleri başka bir bileşene gider.

## <a name="scenario-1-shared-vspackage"></a>Senaryo 1: Paylaşılan VSPackage

Bu senaryoda, paylaşılan bir VSPackage (Visual Studio'nun birden çok sürümü destekleyen tek bir ikili, bir Windows Installer paketinde gönderilir. Visual Studio'nun her sürümüyle kayıt olmak, kullanıcı tarafından seçilebilen özellikler tarafından denetlenir. Ayrıca, ayrı özelliklere atandığında, her bileşenin kurulum veya uninstallation için ayrı ayrı seçilebildiği ve kullanıcının [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage'ı farklı sürümlere entegre etme denetimine dahil edilebildiği anlamına gelir. (Windows Yükleyici paketlerindeki özellikleri kullanma hakkında daha fazla bilgi için [Windows Yükleyici Özellikleri'ne](/windows/desktop/Msi/windows-installer-features) bakın.)

![VS Paylaşılan VSPackage yükleyici](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Resimde gösterildiği gibi, paylaşılan bileşenler her zaman yüklenen Feat_Common özelliğinin bir parçası haline getirilir. Feat_VS2002 ve Feat_VS2003 özelliklerini görünür hale getirerek, kullanıcılar Visual Studio'nun hangi sürümlerinin vspackage'ın entegre olmasını istediklerini yükleme zamanında seçebilirler. Kullanıcılar ayrıca, bu durumda VISUAL Studio'nun farklı sürümlerinden VSPackage kayıt bilgilerini ekleyen veya kaldıran özellikler eklemek veya kaldırmak için Windows Installer bakım modunu da kullanabilir.

> [!NOTE]
> Bir özelliğin Ekran sütununa 0 olarak ayarlanması özelliği gizler. 1 gibi düşük Düzey sütun değeri, her zaman yüklenmesini sağlar. Daha fazla bilgi için [INSTALLLEVEL Özellik](/windows/desktop/Msi/installlevel) ve [Özellik Tablosu'na](/windows/desktop/Msi/feature-table)bakın.

## <a name="scenario-2-shared-vspackage-update"></a>Senaryo 2: Paylaşılan VSPackage Güncelleştirmesi

Bu senaryoda, 1. Tartışma uğruna, güncelleme Visual Studio için destek ekler, ama aynı zamanda basit bir güvenlik yama veya hata düzeltme hizmet paketi olabilir. Windows Installer'ın yeni bileşenleri yükleme kuralları, sistemde zaten bulunan değişmemiş bileşenlerin yeniden kopyalanmaması gerektiğini gerektirir. Bu durumda, sürüm 1.0 zaten mevcut olan bir sistem güncelleştirilmiş bileşeni Comp_MyVSPackage.dll üzerine yazmak ve kullanıcıların bileşeni Comp_VS2005_Reg ile Feat_VS2005 yeni özellik eklemeyi seçmenize izin verir.

> [!CAUTION]
> Bir VSPackage birden fazla sürümü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]arasında paylaşıldığında, VSPackage sonraki sürümleri Visual Studio önceki sürümleri ile geriye dönük uyumluluğu korumak esastır. Geriye dönük uyumluluğu sürdüremediğiniz durumlarda, yan yana, özel VSPackages kullanmanız gerekir. Daha fazla bilgi için Visual [Studio'nun Birden Çok Sürümlerini Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)bölümüne bakın.

![VS Paylaşılan VS Paket Güncelleme yükleyici](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Bu senaryo, Windows Installer'ın küçük yükseltmeler için desteğinden yararlanarak yeni bir VSPackage yükleyici sunar. Kullanıcılar sadece sürüm 1.1 yüklemek ve sürüm 1.0 yükseltir. Ancak, sistemde sürüm 1.0 olması gerekli değildir. Aynı yükleyici sürüm 1.0 olmayan bir sisteme sürüm 1.1 yükler. Bu şekilde küçük yükseltmeleri sağlamak için avantajı bir yükseltme yükleyici ve tam ürün yükleyici geliştirme çalışmaları geçmesi gerekli değildir. Bir yükleyici her iki işi de yapar. Bir güvenlik düzeltmesi veya hizmet paketi bunun yerine Windows Installer yamaları yararlanabilir. Daha fazla bilgi için [Bkz. Yama ve Yükseltmeler.](/windows/desktop/Msi/patching-and-upgrades)

## <a name="scenario-3-side-by-side-vspackage"></a>Senaryo 3: Yan Yana VSPackage

Bu senaryo iki VSPackage yükleyiciler sunar - Visual Studio .NET 2003 ve Visual Studio her sürümü için bir. Her yükleyici yan yana veya özel vspackage (Visual Studio'nun belirli bir sürümü için özel olarak oluşturulmuş ve yüklenmiş bir yüklenir) yükler. Her VSPackage kendi bileşeni bulunmaktadır. Sonuç olarak, her biri yamalar veya bakım sürümleri ile ayrı ayrı servis edilebilir. VSPackage DLL artık sürüme özgü olduğundan, kayıt bilgilerini DLL ile aynı bileşene eklemek güvenlidir.

![VS Yan Yana VS Paket yükleyici](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Her yükleyici, iki yükleyici arasında paylaşılan kodu da içerir. Paylaşılan kod ortak bir konuma yüklenirse, her iki .msi dosyasını yüklemek paylaşılan kodu yalnızca bir kez yükler. İkinci yükleyici bileşene bir başvuru sayısını azaltır. Başvuru sayısı, VSPackages'lerden biri kaldırılırsa paylaşılan kodun diğer VSPackage için kalmasını sağlar. İkinci VSPackage de kaldırılırsa, paylaşılan kod kaldırılır.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Senaryo 4: Yan Yana VSPackage Güncellemesi

Bu senaryoda, Görsel Studio için VSPackage bir güvenlik açığı muzdarip ve bir güncelleştirme sorunu gerekir. Senaryo 2'de olduğu gibi, varolan bir yüklemeyi güvenlik düzeltmesini içerecek şekilde güncelleyen yeni bir .msi dosyası oluşturabilir ve güvenlik düzeltmesi zaten yerinde olan yeni yüklemeleri dağıtabilirsiniz.

Bu durumda, VSPackage yönetilen bir VSPackage küresel montaj önbelleğinde (GAC) yüklenir. Güvenlik düzeltmesini içerecek şekilde yeniden yeniden yapılandırdığınızda, derleme sürüm numarasının düzeltme numarası bölümünü değiştirmeniz gerekir. Yeni montaj sürüm numarasının kayıt bilgileri önceki sürümün [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] üzerine yazarak sabit montajın yüklenmesine neden olur.

![VS Yan Yana VS Paket Güncelleme yükleyici](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Yan yana derlemelerin dağıtımı hakkında daha fazla bilgi için [,.NET Framework ile Dağıtımı Basitleştirme ve DLL Cehennemini Çözme bölümüne](https://msdn.microsoft.com/library/ms973843.aspx)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Visual Studio'nun Birden Çok Sürümünü Destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
