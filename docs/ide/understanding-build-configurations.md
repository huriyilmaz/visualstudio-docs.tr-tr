---
title: Derleme yapılandırmalarını anlama
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21421776506868942e9dc562db4f456c2012fce7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592028"
---
# <a name="understand-build-configurations"></a>Derleme yapılandırmalarını anlama

Farklı türlerde derlemelerde kullanmak üzere çözüm ve proje özelliklerinin farklı yapılandırmalarının depolanmasını sağlayabilirsiniz. Bir yapılandırma oluşturmak, seçmek, değiştirmek veya silmek için **Configuration Manager**kullanabilirsiniz. Açmak için, menü çubuğunda **Configuration Manager** > **Oluştur** ' u seçin veya arama kutusuna **yapılandırma** yazın. Bir yapılandırma seçmek veya **Configuration Manager**açmak için **Standart** araç çubuğundaki **çözüm yapılandırmaları** listesini de kullanabilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio derleme yapılandırması](/visualstudio/mac/configurations).

> [!NOTE]
> Araç çubuğunda çözüm yapılandırma ayarlarını bulamazsanız ve **Configuration Manager**erişemeyebilirsiniz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geliştirme ayarları uygulanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic Geliştirici ayarları uygulanmış konfigürasyonları yönetme](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Varsayılan olarak, hata ayıklama ve sürüm yapılandırmalarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] şablonlar kullanılarak oluşturulan projelere dahildir. Bir hata ayıklama yapılandırması, bir uygulamanın hata ayıklamasını destekler ve bir sürüm yapılandırması, uygulamasının dağıtılabilecek bir sürümünü oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md). Ayrıca, özel çözüm konfigürasyonları ve proje yapılandırması da oluşturabilirsiniz. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Çözüm yapılandırması

Çözüm yapılandırması, çözümdeki projelerin nasıl oluşturulup dağıtılacağını belirler. Bir çözüm yapılandırmasını değiştirmek veya yeni bir tane tanımlamak için **Configuration Manager**, **etkin çözüm yapılandırması**altında **Düzenle** veya **Yeni**' yi seçin.

Bir çözüm yapılandırmasındaki **Proje bağlamları** kutusundaki her giriş çözümdeki bir projeyi temsil eder. **Etkin çözüm yapılandırması** ve **etkin çözüm platformunun**her birleşimi için, her projenin nasıl kullanıldığını belirleyebilirsiniz. (Çözüm platformları hakkında daha fazla bilgi için bkz. [derleme platformlarını anlama](../ide/understanding-build-platforms.md).)

> [!NOTE]
> Yeni bir çözüm yapılandırması tanımladığınızda ve **Yeni proje yapılandırmaları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak yeni yapılandırmayı projelere atar. Benzer şekilde, yeni bir çözüm platformu tanımlayıp **Yeni proje platformları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak yeni platformu projelere atar. Ayrıca, yeni platformu hedefleyen bir proje eklerseniz, Visual Studio bu platformu çözüm platformları listesine ekler ve bunu tüm projelere atar.
>
> Her projenin ayarlarını yine de değiştirebilirsiniz.

Etkin çözüm yapılandırması, IDE için de bağlam sağlar. Örneğin, bir proje üzerinde çalışıyorsanız ve yapılandırma bir mobil cihaz için derlendiğini belirtiyorsa, **araç kutusu** yalnızca bir mobil cihaz projesinde kullanılabilecek öğeleri görüntüler.

## <a name="project-configurations"></a>Proje yapılandırması
Bir projenin hedeflediği yapılandırma ve platform, derlendiklerinde kullanılacak özellikleri belirtmek için birlikte kullanılır. Bir proje, her yapılandırma ve platformun birleşimi için farklı bir özellik tanımları kümesine sahip olabilir. Bir projenin özelliklerini değiştirmek için, özellik sayfalarını kullanabilirsiniz. ( **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.)

Her proje yapılandırması için gerektiğinde yapılandırmaya bağımlı özellikler tanımlayabilirsiniz. Örneğin, belirli bir yapı için hangi proje öğelerinin ekleneceğini ve hangi çıkış dosyalarının oluşturulacağını, nereye yerleştirileceğini ve bunların nasıl iyileştireedileceğini belirleyebilirsiniz.

Proje konfigürasyonları önemli ölçüde farklılık gösterebilir. Örneğin, bir yapılandırmanın özellikleri, çıkış dosyasının minimum alanı kaplamaya en iyi duruma getirilmiş olduğunu belirtebilir, ancak başka bir yapılandırma yürütülebilir dosyasının en yüksek hızda çalıştığını belirtebilir.

Proje konfigürasyonları, bir ekip tarafından paylaşılabilmesi için kullanıcıya göre değil, çözüme göre saklanır.

Proje bağımlılıkları, yapılandırmaya bağımsız olsa da, yalnızca etkin çözüm yapılandırmasında belirtilen projeler oluşturulur.

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio proje yapılandırmasını nasıl atar
Yeni bir çözüm yapılandırması tanımladığınızda ve ayarları var olan bir sunucudan kopyalamazsanız, Visual Studio varsayılan proje yapılandırmalarını atamak için aşağıdaki ölçütleri kullanır. Ölçütler gösterilen sırayla değerlendirilir.

1. Bir proje, yeni çözüm yapılandırmasının adıyla tam olarak eşleşen bir yapılandırma adına ( *\<yapılandırma adı > \<platform adı >* ) sahipse, bu yapılandırma atanır. Yapılandırma adları büyük/küçük harfe duyarlı değildir.

2. Projenin, yapılandırma adı bölümünün yeni çözüm yapılandırmasıyla eşleştiği bir yapılandırma adı varsa, bu yapılandırma atanır ve platform bölümünün eşleşip eşleşmediğini belirtir.

3. Hala eşleşme yoksa, projede listelenen ilk yapılandırma atanır.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 'Nun çözüm yapılandırması nasıl atanır
Bir proje yapılandırması oluşturduğunuzda ( **Configuration Manager**, bu projenin **yapılandırma** sütunundaki açılan menüde **Yeni** ' yi seçerek) ve **yeni çözüm yapılandırmaları oluştur** onay kutusunu işaretlediğinizde, Visual Studio desteklediği her platformda projeyi derlemek için benzer adlı bir çözüm yapılandırması arar. Bazı durumlarda, Visual Studio mevcut çözüm yapılandırmalarının adını değiştirir veya yenilerini tanımlar.

Visual Studio, çözüm yapılandırması atamak için aşağıdaki ölçütleri kullanır.

- Bir proje yapılandırması bir platform belirtmezse veya yalnızca bir platform belirtirse, adı yeni proje yapılandırmasıyla eşleşen bir çözüm yapılandırması bulundu veya eklendi. Bu çözüm yapılandırmasının varsayılan adı bir platform adı içermez; form *\<proje yapılandırma adı >* alır.

- Bir proje birden çok platformu destekliyorsa, desteklenen her platform için bir çözüm yapılandırması bulunur ya da eklenir. Her çözüm yapılandırmasının adı hem proje yapılandırma adını hem de platform adını içerir ve form *\<proje yapılandırma adı > \<platform adı >* içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ derleme başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [Derleme konfigürasyonları (Mac için Visual Studio)](/visualstudio/mac/configurations)
