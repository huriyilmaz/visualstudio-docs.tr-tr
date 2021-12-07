---
title: Derleme yapılandırmalarını anlama
description: Projelerinizi farklı ayarlarla derlemeniz gerekirken derleme yapılandırmalarını nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/06/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4308f1e49f531e0d7cb486d483e338fd234eb9e
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977578"
---
# <a name="understand-build-configurations"></a>Derleme yapılandırmalarını anlama

Projelerinizi farklı ayarlarla derlemeniz gereken derleme yapılandırmaları gerekir. Örneğin, **Hata Ayıklama ve** **Yayın** yapılandırmalardır ve bunları derlemek için farklı derleyici seçenekleri kullanılır.  Yapılandırmalardan biri etkindir ve IDE'nin üst kısmında yer alan komut çubuğunda belirtilmiştir.

:::moniker range="<=vs-2019"
![Ana araç çubuğunda etkin yapılandırmayı gösteren Visual Studio görüntüsü.](media/understanding-build-configurations/active-config.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Ana araç çubuğunda etkin yapılandırmayı gösteren Visual Studio görüntüsü.](media/vs-2022/build-configurations-active-config.png)
:::moniker-end

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/configurations)

Yapılandırma ve yerleşik çıkış dosyalarının depolandığı platform denetimi. Normalde, Visual Studio projenizi yapılandırmasını yapılandırmasını (örneğin, *bin/Debug/x86)* ile adlı bir proje alt klasörüne yerleştirilir, ancak bunu değiştirebilirsiniz.

Çözüm ve proje düzeyinde kendi derleme yapılandırmalarınızı oluşturabilirsiniz. Çözüm yapılandırması, yapılandırma etkin olduğunda derlemeye hangi projelerin dahil olduğunu belirler. Yalnızca etkin çözüm yapılandırmasında belirtilen projeler hazırlar. Bu platformda birden çok Yapılandırma Yöneticisi platform seçilirse, bu platform için geçerli olan tüm projeler yerleşiktir. Proje yapılandırması, projeyi derlerken hangi derleme ayarlarının ve derleyici seçeneklerinin kullanılacaklarını belirler.

Bir yapılandırmayı oluşturmak, seçmek, değiştirmek veya silmek için **Yapılandırma Yöneticisi.** Açmak için menü çubuğunda Derleme ve oluşturma'Yapılandırma Yöneticisi  >  seçin veya arama kutusuna **Yapılandırma** yazın. Bir yapılandırma seçmek için **Standart araç** çubuğundaki **Çözüm** Yapılandırmaları listesini de kullanabilir veya **Yapılandırma Yöneticisi.**

![Yapılandırma Yöneticisi ekran görüntüsü.](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Araç çubuğunda çözüm yapılandırma ayarlarını bulamıyorsanız ve Yapılandırma Yöneticisi erişe **Yapılandırma Yöneticisi** geliştirme ayarlarını kullanıyor [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] olabilir. Daha fazla bilgi için [bkz. Nasıl yapılır: Uygulamanın uygulandığı Visual Basic yapılandırmaları yönetme.](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)

Varsayılan olarak, **Hata Ayıklama** **ve Yayın** yapılandırmaları şablonlar kullanılarak oluşturulan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projelere dahil edilir. Hata **ayıklama yapılandırması** bir uygulamanın hata ayıklamasını destekler ve Yayın yapılandırması, uygulamanın dağıtılabilir bir sürümünü derlemenizi sağlar.  Daha fazla bilgi için, [bkz. How to: Set debug and release configurations](../debugger/how-to-set-debug-and-release-configurations.md). Ayrıca özel çözüm yapılandırmaları ve proje yapılandırmaları da oluşturabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Çözüm yapılandırmaları

Çözüm yapılandırması, çözümde projelerin nasıl üret ve dağıtılacaklarını belirtir. Bir çözüm yapılandırmasını değiştirmek veya yeni bir tane tanımlamak için, Yapılandırma Yöneticisi **altında** Etkin çözüm yapılandırması altında **Düzenle** **veya Yeni'yi** **seçin.**

Çözüm yapılandırmasında **Project kutusunda yer** alan her giriş, çözümde bir projeyi temsil eder. Etkin çözüm **yapılandırmasının ve Etkin çözüm** **platformunun her** birleşimi için, her projenin nasıl kullanılacaklarını ayarlayın. (Çözüm platformları hakkında daha fazla bilgi için bkz. [Derleme platformlarını anlama.)](../ide/understanding-build-platforms.md)

Yeni bir çözüm yapılandırması tanımladığınız ve Yeni proje **yapılandırmaları** oluştur onay kutusunu işaretle işaretlenirken, yeni yapılandırmayı otomatik olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tüm projelere atar. Benzer şekilde, yeni bir çözüm platformu  tanımladığınız ve Yeni proje platformları oluştur onay kutusunu işaretle hazırladığınız zaman, yeni platformu tüm [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projelere otomatik olarak atar. Ayrıca, yeni bir platformu hedef alan bir proje ekler Visual Studio platformunu çözüm platformları listesine ekler ve tüm projelere atar. Yine de her projenin ayarlarını değiştirebilirsiniz.

Etkin çözüm yapılandırması, IDE için bağlam da sağlar. Örneğin, bir proje üzerinde çalışıyorsanız ve yapılandırma bunun bir mobil cihaz için hazır  olacağını belirtirse, Araç Kutusu yalnızca bir mobil cihaz projesinde kullanılmaktadır öğeleri görüntüler.

## <a name="project-configurations"></a>Project yapılandırmaları

Projenin hedeflediği yapılandırma ve platform, derlenmiş olduğunda kullanılacak derleme ayarlarını ve derleyici seçeneklerini belirtmek için birlikte kullanılır. Bir projenin her yapılandırma ve platform bileşimi için farklı ayarları olabilir. Projenin özelliklerini değiştirmek için proje kısayol menüsünü Çözüm Gezgini **'de** açın ve özellikler'i **seçin.**  Proje tasarımcısının **Derleme sekmesinin** üst kısmında, derleme ayarlarını düzenlemek için etkin bir yapılandırma seçin.

:::moniker range="<=vs-2019"
![Proje tasarımcısı yapılandırmalarının ekran görüntüsü.](media/understanding-build-configurations/project-designer-configuration.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Proje tasarımcısı yapılandırmalarının ekran görüntüsü.](media/vs-2022/build-configuration-project-designer-configuration.png)
:::moniker-end

## <a name="building-multiple-configurations"></a>Birden çok yapılandırma oluşturma

Derleme Çözümü komutunu kullanarak bir **çözüm**  >  **derlemek** Visual Studio yalnızca etkin yapılandırmayı derlemez. Bu çözüm yapılandırmasında belirtilen tüm projeler ve tek proje yapılandırması, etkin çözüm yapılandırmasında ve etkin çözüm platformunda belirtilen proje yapılandırmasıdır ve bu yapılandırma, Visual Studio. Örneğin, **Hata Ayıkla ve** **x86**. Diğer tanımlı yapılandırmalar ve platformlar yerleşik değildir.

Birden çok yapılandırmayı ve platformu tek bir eylemde derlemek için toplu iş derleme  >  **seçeneğini** Visual Studio. Bu özelliye erişmek için **Ctrl** + **Q** tuşlarına basarak arama kutusunu açın ve `Batch build` yazın. Batch derlemesi tüm proje türleri için kullanılamaz. Bkz. [Nasıl kullanılır: Aynı anda birden çok yapılandırma oluşturma.](how-to-build-multiple-configurations-simultaneously.md)

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio yapılandırmalarını atama

Yeni bir çözüm yapılandırması tanımlayıp mevcut bir çözümden ayarları kopyalamadığınız zaman, Visual Studio proje yapılandırmalarını atamak için aşağıdaki ölçütleri kullanır. Ölçütler gösterilen sırayla değerlendirilir.

1. Projenin yeni çözüm yapılandırmasının *\<configuration name> \<platform name>* adıyla tam olarak eşleşen bir yapılandırma adı ( ) varsa, bu yapılandırma atanır. Yapılandırma adları büyük/büyük/büyük harfe duyarlı değildir.

1. Proje, yapılandırma adı bölümünün yeni çözüm yapılandırmasıyla eş olduğu bir yapılandırma adına sahipse platform bölümü eşlese de eşleşmese de bu yapılandırma atanır.

1. Hala eşleşme yoksa, projede listelenen ilk yapılandırma atanır.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Çözüm Visual Studio yapılandırmalarını atama

Bir proje yapılandırması ekleyebilirsiniz **(Yapılandırma Yöneticisi'da,** ilgili  projenin Yapılandırma sütunundaki açılan  menüde Yeni'yi seçerek) ve Yeni çözüm yapılandırmaları oluştur onay kutusunu işaretleyip, Visual Studio projeyi desteklediği her platformda oluşturmak için benzer adlı bir çözüm yapılandırmasına göz atabilirsiniz.  Bazı durumlarda, Visual Studio çözüm yapılandırmalarını yeniden adlandırarak veya yenilerini tanımlar.

Visual Studio yapılandırmaları atamak için aşağıdaki ölçütleri kullanır.

- Proje yapılandırması bir platform belirtmezseniz veya yalnızca bir platform belirtmezseniz, adı yeni proje yapılandırmasıyla eşleşen bir çözüm yapılandırması bulunur veya eklenir. Bu çözüm yapılandırmasının varsayılan adı bir platform adı içermemektedir; , formunu *\<project configuration name>* alır.

- Bir proje birden çok platformu destekliyorsa, desteklenen her platform için bir çözüm yapılandırması bulunur veya eklenir. Her çözüm yapılandırmasının adı hem proje yapılandırma adını hem de *\<project configuration name> \<platform name>* platform adını içerir ve şeklindedir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ derleme başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Derleme platformlarını anlama](understanding-build-platforms.md)
- [Derleme yapılandırmaları (Mac için Visual Studio)](/visualstudio/mac/configurations)
