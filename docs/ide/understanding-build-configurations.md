---
title: Derleme yapılandırmalarını anlama
ms.date: 01/20/2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904171"
---
# <a name="understand-build-configurations"></a>Derleme yapılandırmalarını anlama

Projelerinizi farklı ayarlarla oluşturmanız gerektiğinde derleme yapılandırmalarına ihtiyacınız vardır. Örneğin, **hata ayıklama** ve **yayın** yapılandırma ve farklı derleyici seçenekleri bunları oluştururken uygun şekilde kullanılır.  Bir yapılandırma etkindir ve IDE 'nin en üstündeki komut çubuğunda gösterilir.

![Etkin yapılandırma](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio derleme yapılandırması](/visualstudio/mac/configurations).

Oluşturulan çıkış dosyalarının depolandığı yapılandırma ve platform denetimi. Normalde, Visual Studio projenizi oluşturduğunda çıktı, etkin yapılandırma (örneğin, *bin/Debug/x86*) adlı bir proje alt klasörüne yerleştirilir, ancak bunu değiştirebilirsiniz.

Çözüm ve proje düzeyinde kendi yapı yapılandırmalarınızı oluşturabilirsiniz. Çözüm yapılandırması, yapılandırma etkin olduğunda hangi projelerin yapıya ekleneceğini belirler. Yalnızca etkin çözüm yapılandırmasında belirtilen projeler oluşturulur. Configuration Manager birden çok hedef platform seçildiyse, o platformda uygulanan tüm projeler oluşturulur. Proje yapılandırması, projeyi oluştururken hangi derleme ayarlarının ve derleyici seçeneklerinin kullanıldığını belirler.

Bir yapılandırma oluşturmak, seçmek, değiştirmek veya silmek için **Configuration Manager**kullanabilirsiniz. Açmak için, menü çubuğunda **Configuration Manager** > **Oluştur** ' u seçin veya arama kutusuna **yapılandırma** yazın. Bir yapılandırma seçmek veya **Configuration Manager**açmak için **Standart** araç çubuğundaki **çözüm yapılandırmaları** listesini de kullanabilirsiniz.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Araç çubuğunda çözüm yapılandırma ayarlarını bulamazsanız ve **Configuration Manager**erişemeyebilirsiniz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geliştirme ayarları uygulanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic Geliştirici ayarları uygulanmış konfigürasyonları yönetme](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Varsayılan olarak, **hata ayıklama** ve **Sürüm** yapılandırmalarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] şablonlar kullanılarak oluşturulan projelere dahildir. Bir **hata ayıklama** yapılandırması, bir uygulamanın hata ayıklamasını destekler ve bir **Sürüm** yapılandırması, uygulamasının dağıtılabilecek bir sürümünü oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md). Ayrıca, özel çözüm konfigürasyonları ve proje yapılandırması da oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Çözüm yapılandırması

Çözüm yapılandırması, çözümdeki projelerin nasıl oluşturulup dağıtılacağını belirler. Bir çözüm yapılandırmasını değiştirmek veya yeni bir tane tanımlamak için **Configuration Manager**, **etkin çözüm yapılandırması**altında **Düzenle** veya **Yeni**' yi seçin.

Bir çözüm yapılandırmasındaki **Proje bağlamları** kutusundaki her giriş çözümdeki bir projeyi temsil eder. **Etkin çözüm yapılandırması** ve **etkin çözüm platformunun**her birleşimi için, her projenin nasıl kullanıldığını belirleyebilirsiniz. (Çözüm platformları hakkında daha fazla bilgi için bkz. [derleme platformlarını anlama](../ide/understanding-build-platforms.md).)

Yeni bir çözüm yapılandırması tanımladığınızda ve **Yeni proje yapılandırmaları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak yeni yapılandırmayı projelere atar. Benzer şekilde, yeni bir çözüm platformu tanımlayıp **Yeni proje platformları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak yeni platformu projelere atar. Ayrıca, yeni platformu hedefleyen bir proje eklerseniz, Visual Studio bu platformu çözüm platformları listesine ekler ve bunu tüm projelere atar. Her projenin ayarlarını yine de değiştirebilirsiniz.

Etkin çözüm yapılandırması, IDE için de bağlam sağlar. Örneğin, bir proje üzerinde çalışıyorsanız ve yapılandırma bir mobil cihaz için derlendiğini belirtiyorsa, **araç kutusu** yalnızca bir mobil cihaz projesinde kullanılabilecek öğeleri görüntüler.

## <a name="project-configurations"></a>Proje yapılandırması

Bir projenin hedeflediği yapılandırma ve platform, derleme ayarlarını ve derlendiklerinde kullanılacak derleyici seçeneklerini belirtmek için birlikte kullanılır. Bir proje, her yapılandırma ve platformun birleşimi için farklı ayarlara sahip olabilir. Bir projenin özelliklerini değiştirmek için **Çözüm Gezgini**' de proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  Proje Tasarımcısı 'nın **Build** sekmesinin en üstünde, yapı ayarlarını düzenlemek için etkin bir yapılandırma seçin.

![Proje Tasarımcısı yapılandırması](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Birden çok yapılandırma oluşturma

**Build** > **Build Solution** komutunu kullanarak bir çözüm oluşturduğunuzda, Visual Studio yalnızca etkin yapılandırmayı oluşturur. Bu çözüm yapılandırmasında belirtilen tüm projeler oluşturulmuştur ve oluşturulan tek proje yapılandırması, Visual Studio 'da araç çubuğunda gösterilen etkin çözüm yapılandırmasında ve etkin çözüm platformunda belirtidir. Örneğin, **Hata Ayıkla** ve **x86**. Diğer tanımlı yapılandırma ve platformlar derlenmez.

Tek bir eylemde birden çok yapılandırma ve platform oluşturmak istiyorsanız, Visual Studio 'da **build** > **Batch Build** seçeneğini kullanabilirsiniz. Bu özelliğe erişmek için **Ctrl**+**Q** tuşlarına basarak arama kutusunu açın ve `Batch build`girin. Toplu derleme tüm proje türleri için kullanılamaz. Bkz. [nasıl yapılır: aynı anda birden çok yapılandırma oluşturma](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio proje yapılandırmasını nasıl atar

Yeni bir çözüm yapılandırması tanımladığınızda ve ayarları var olan bir sunucudan kopyalamazsanız, Visual Studio varsayılan proje yapılandırmalarını atamak için aşağıdaki ölçütleri kullanır. Ölçütler gösterilen sırayla değerlendirilir.

1. Bir proje, yeni çözüm yapılandırmasının adıyla tam olarak eşleşen bir yapılandırma adına ( *\<yapılandırma adı > \<platform adı >* ) sahipse, bu yapılandırma atanır. Yapılandırma adları büyük/küçük harfe duyarlı değildir.

1. Projenin, yapılandırma adı bölümünün yeni çözüm yapılandırmasıyla eşleştiği bir yapılandırma adı varsa, bu yapılandırma atanır ve platform bölümünün eşleşip eşleşmediğini belirtir.

1. Hala eşleşme yoksa, projede listelenen ilk yapılandırma atanır.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 'Nun çözüm yapılandırması nasıl atanır

Bir proje yapılandırması oluşturduğunuzda ( **Configuration Manager**, bu projenin **yapılandırma** sütunundaki açılan menüde **Yeni** ' yi seçerek) ve **yeni çözüm yapılandırmaları oluştur** onay kutusunu işaretlediğinizde, Visual Studio desteklediği her platformda projeyi derlemek için benzer adlı bir çözüm yapılandırması arar. Bazı durumlarda, Visual Studio mevcut çözüm yapılandırmalarının adını değiştirir veya yenilerini tanımlar.

Visual Studio, çözüm yapılandırması atamak için aşağıdaki ölçütleri kullanır.

- Bir proje yapılandırması bir platform belirtmezse veya yalnızca bir platform belirtirse, adı yeni proje yapılandırmasıyla eşleşen bir çözüm yapılandırması bulundu veya eklendi. Bu çözüm yapılandırmasının varsayılan adı bir platform adı içermez; form *\<proje yapılandırma adı >* alır.

- Bir proje birden çok platformu destekliyorsa, desteklenen her platform için bir çözüm yapılandırması bulunur ya da eklenir. Her çözüm yapılandırmasının adı hem proje yapılandırma adını hem de platform adını içerir ve form *\<proje yapılandırma adı > \<platform adı >* içerir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ derleme başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Derleme konfigürasyonları (Mac için Visual Studio)](/visualstudio/mac/configurations)
