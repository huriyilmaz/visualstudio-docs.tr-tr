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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904171"
---
# <a name="understand-build-configurations"></a>Derleme yapılandırmalarını anlama

Projelerinizi farklı ayarlarla oluşturmanız gerektiğinde yapı yapılandırmalarına ihtiyacınız vardır. Örneğin, **Hata Ayıklama** ve **Sürüm** yapılandırmalardır ve bunları yaparken buna göre farklı derleyici seçenekleri kullanılır.  Bir yapılandırma etkindir ve IDE'nin üst kısmındaki komut çubuğunda gösterilir.

![Etkin yapılandırma](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'da Yapı yapılandırmaları'na](/visualstudio/mac/configurations)bakın.

Yapılı çıktı dosyalarının depolandığı yapılandırma ve platform denetimi. Normalde, Visual Studio projenizi oluşturduğunda, çıktı etkin yapılandırmayla (örneğin, *bin/Debug/x86)* adlı bir proje alt klasörüne yerleştirilir, ancak bunu değiştirebilirsiniz.

Çözüm ve proje düzeyinde kendi yapı yapılandırmalarınızı oluşturabilirsiniz. Çözüm yapılandırması, yapılandırma etkin olduğunda yapıya hangi projelerin dahil edildiğini belirler. Yalnızca etkin çözüm yapılandırmasında belirtilen projeler oluşturulur. Configuration Manager'da birden çok hedef platform seçilirse, bu platforma uygulanan tüm projeler oluşturulur. Proje yapılandırması, projeyi oluştururken hangi yapı ayarlarının ve derleyici seçeneklerinin kullanılacağını belirler.

Yapılandırma oluşturmak, seçmek, değiştirmek veya silmek için **Configuration Manager'ı**kullanabilirsiniz. Açmak için menü çubuğunda > **Yapı Yapılandırma Yöneticisi'ni** **seçin**veya arama kutusuna **Yapılandırma** yazın. Yapılandırma seçmek veya **Configuration Manager'ı**açmak için **Standart** araç çubuğundaki **Çözüm Yapılandırmaları** listesini de kullanabilirsiniz.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Araç çubuğunda çözüm yapılandırma ayarlarını bulamıyorsanız ve **Configuration Manager'a**erişemiyorsanız, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] geliştirme ayarları uygulanabilir. Daha fazla bilgi için [bkz: Visual Basic geliştirici ayarları uygulanmış yapılandırmaları yönetme.](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)

Varsayılan olarak, **Hata Ayıklama** ve **Sürüm** yapılandırmaları şablonlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanılarak oluşturulan projelere dahildir. **Hata Ayıklama** yapılandırması bir uygulamanın hata ayıklamasını destekler ve **Sürüm** yapılandırması uygulamanın dağıtılabilen bir sürümünü oluşturur. Daha fazla bilgi için [bkz: Hata ayıklama ve sürüm yapılandırmaları ayarlayın.](../debugger/how-to-set-debug-and-release-configurations.md) Ayrıca özel çözüm yapılandırmaları ve proje yapılandırmaları oluşturabilirsiniz. Daha fazla bilgi için [bkz: Yapılandırmalar oluşturun ve düzenleme.](../ide/how-to-create-and-edit-configurations.md)

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Çözüm yapılandırması, çözümdeki projelerin nasıl oluşturulup dağıtılaneceğini belirtir. Bir çözüm yapılandırmasını değiştirmek veya Configuration **Manager'da,** **Etkin çözüm yapılandırması**altında yeni bir yapılandırma tanımlamak **için, Düzenleme** veya **Yeni'yi**seçin.

**Çözüm yapılandırmasındaki Proje bağlamları** kutusundaki her giriş, çözümdeki bir projeyi temsil eder. Etkin çözüm **yapılandırması** ve **Etkin çözüm platformunun**her birleşimi için, her projenin nasıl kullanıldığını ayarlayabilirsiniz. (Çözüm platformları hakkında daha fazla bilgi için [bkz.](../ide/understanding-build-platforms.md)

Yeni bir çözüm yapılandırması tanımladığınızda ve **Yeni proje yapılandırmaları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yeni yapılandırmayı tüm projelere otomatik olarak atarsınız. Aynı şekilde, yeni bir çözüm platformu tanımladığınızda ve **yeni proje platformları oluştur** onay kutusunu seçtiğinizde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yeni platformu tüm projelere otomatik olarak atarsınız. Ayrıca, yeni bir platformu hedefleyen bir proje eklerseniz, Visual Studio bu platformu çözüm platformları listesine ekler ve tüm projelere atar. Yine de her proje için ayarları değiştirebilirsiniz.

Etkin çözüm yapılandırması, IDE'ye bağlam da sağlar. Örneğin, bir proje üzerinde çalışıyorsanız ve yapılandırma bir mobil aygıt için oluşturulacağını belirtirse, **Araç Kutusu** yalnızca bir mobil aygıt projesinde kullanılabilecek öğeleri görüntüler.

## <a name="project-configurations"></a>Proje yapılandırmaları

Proje hedeflediğinde kullanılacak yapı ayarlarını ve derleyici seçeneklerini belirtmek için birlikte kullanılan yapılandırma ve platform. Bir proje, yapılandırma ve platformun her birleşimi için farklı ayarlara sahip olabilir. Projenin özelliklerini değiştirmek **için, Çözüm Gezgini'nde**projenin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.  Proje tasarımcısının **Yapı** sekmesinin üst kısmında, yapı ayarlarını düzenlemek için etkin bir yapılandırma seçin.

![Proje tasarımcısı yapılandırmaları](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Birden çok yapılandırma oluşturma

**Yapı** > **Çözümü** komutunu kullanarak bir çözüm oluşturduğunuzda, Visual Studio yalnızca etkin yapılandırmayı oluşturur. Bu çözüm yapılandırmasında belirtilen tüm projeler oluşturulur ve yapılan tek proje yapılandırması, Visual Studio'daki araç çubuğunda gösterilen etkin çözüm yapılandırması ve etkin çözüm platformunda belirtilen proje yapılandırmasıdır. Örneğin, **Hata Ayıklama** ve **x86**. Diğer tanımlanmış yapılandırmalar ve platformlar oluşturulmaz.

Tek bir eylemde birden çok yapılandırma ve platform oluşturmak istiyorsanız, Visual Studio'da **Toplu Oluşturma** > **Yap** seçeneğini kullanabilirsiniz. Bu özelliğe erişmek için arama kutusunu açmak için `Batch build` **Ctrl**+**Q** tuşuna basın ve . Toplu oluşturma tüm proje türleri için kullanılamaz. [Bkz. Nasıl Yapılacağını: Aynı anda birden çok yapılandırma oluşturun.](how-to-build-multiple-configurations-simultaneously.md)

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio proje yapılandırmalarını nasıl atar?

Yeni bir çözüm yapılandırması tanımladığınızda ve ayarları varolan bir yapılandırmadan kopyalamadığınızda, Visual Studio varsayılan proje yapılandırmalarını atamak için aşağıdaki ölçütleri kullanır. Ölçütler gösterilen sırada değerlendirilir.

1. Bir projenin yeni çözüm yapılandırmasının adıyla tam olarak eşleşen bir yapılandırma adı*\<(yapılandırma adı> \<platform adı>) *varsa, bu yapılandırma atanır. Yapılandırma adları büyük/küçük harf duyarlı değildir.

1. Projede yapılandırma adı bölümünün yeni çözüm yapılandırmasıile eşleştiğini belirten bir yapılandırma adı varsa, platform bölümü eşleşse de eşleşmese de bu yapılandırma atanır.

1. Eşleşme yoksa, projede listelenen ilk yapılandırma atanır.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio çözüm yapılandırmalarını nasıl atar?

Bir proje yapılandırması oluşturduğunuzda **(Configuration Manager'da**, bu proje için **Yapılandırma** sütunundaki açılır menüde **Yeni'yi** seçerek) ve Yeni **çözüm yapılandırmaları oluştur** onay kutusunu seçtiğinizde, Visual Studio projeyi desteklediği her platformda oluşturmak için benzer adlandırılmış bir çözüm yapılandırması arar. Bazı durumlarda, Visual Studio varolan çözüm yapılandırmalarını yeniden adlandırır veya yeni yapılandırmaları tanımlar.

Visual Studio çözüm yapılandırmaları atamak için aşağıdaki ölçütleri kullanır.

- Proje yapılandırması bir platform belirtmiyorsa veya tek bir platform belirtmiyorsa, adı yeni proje yapılandırmasının adı yla eşleşen veya bulunan veya eklenen bir çözüm yapılandırması. Bu çözüm yapılandırmasının varsayılan adı bir platform adı içermez; form proje * \<yapılandırma adını>* alır.

- Proje birden çok platformu destekliyorsa, desteklenen her platform için bir çözüm yapılandırması bulunur veya eklenir. Her çözüm yapılandırmasının adı hem proje yapılandırma adını hem de platform adını içerir ve form * \<proje yapılandırması adı> \<platform adı>. *

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ derleme başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Yapı platformlarını anlama](understanding-build-platforms.md)
- [Yapılandırmalar oluşturma (Mac için Visual Studio)](/visualstudio/mac/configurations)
