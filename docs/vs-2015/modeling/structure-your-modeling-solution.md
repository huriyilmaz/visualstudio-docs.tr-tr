---
title: Modelleme çözümünüzü yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83c8d8e7a1afe0946c1b1f5eb25c8650e2b512f5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917323"
---
# <a name="structure-your-modeling-solution"></a>Modelleme çözümünüzün yapısını oluşturma

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir geliştirme projesinde modelleri etkin bir şekilde kullanmak için, takım üyelerinin projenin farklı bölümlerinin modelleriyle aynı anda çalışabilebilmesi gerekir. Bu konu başlığı altında, uygulamayı genel bir katman diyagramındaki katmanlara karşılık gelen farklı bölümlere bölmek için bir düzen önerilir.

Bir projede veya alt projede hızlı bir şekilde başlamak için, seçtiğiniz proje yapısını izleyen bir proje şablonu olması yararlı olur. Bu konu, böyle bir şablonun nasıl oluşturulacağını ve kullanılacağını açıklar.

Bu konu, birkaç takım üyesi gerektirecek kadar büyük bir proje üzerinde çalıştığınızı ve belki de birçok takıma sahip olduğunu varsayar. Projenin kodu ve modelleri [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]gibi bir kaynak denetimi sisteminde depolanır. En az bazı takım üyeleri, model geliştirmek için Visual Studio kullanır ve diğer takım üyeleri diğer Visual Studio sürümlerini kullanarak modelleri görüntüleyebilir.

Hangi Visual Studio sürümlerinin her bir aracı ve modelleme özelliğini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Çözüm yapısı

Orta veya büyük bir projede, ekibin yapısı uygulamanın yapısına göre belirlenir. Her takım bir Visual Studio çözümü kullanır.

#### <a name="to-divide-an-application-into-layers"></a>Bir uygulamayı katmanlara bölmek için

1. Web uygulaması, hizmet uygulaması veya masaüstü uygulaması gibi, çözümünüzün yapısını uygulamanızın yapısına dayandırın. Birçok yaygın [mimaride, Microsoft uygulama mimarisi Kılavuzu 'Ndaki uygulama arşiv türleri](/previous-versions/msp-n-p/ee658107(v=pandp.10))bölümünde açıklanmaktadır.

2. Mimari çözümünü çağıracağız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü oluşturun. Bu çözüm, sistemin genel tasarımını oluşturmak için kullanılacaktır. Modeller içerir, ancak kod içermez.

    Bu çözüme bir katman diyagramı ekleyin. Katman diyagramında, uygulamanız için seçtiğiniz mimariyi çizin. Örneğin, diyagram bu katmanları ve bunlar arasındaki bağımlılıkları gösterebilir: sunum; İş mantığı; ve verileri.

    **Mimari** MENÜSÜNDEKI **Yeni UML veya katman diyagramı** komutunu kullanarak katman diyagramını ve yeni bir Visual Studio çözümünü aynı anda oluşturabilirsiniz.

3. Önemli iş kavramlarını temsil eden mimari modeli UML diyagramlarına ekleyin ve tüm katmanların tasarımında başvurulan servis taleplerini kullanın.

4. Mimari katman diyagramında her katman için ayrı bir Visual Studio çözümü oluşturun.

    Bu çözümler katmanların kodunu geliştirmek için kullanılacaktır.

5. Katmanların ve tüm katmanlarda ortak olan kavramların tasarımlarını temsil edecek UML modelleri oluşturun. Tüm modellerin mimari çözümden görünebilmesi ve ilgili modellerin her katmandan görünebilmesi için modelleri düzenleyin.

    Bunu, aşağıdaki yordamlardan birini kullanarak elde edebilirsiniz. İlk alternatif, her katman için ayrı bir modelleme projesi oluşturur ve ikincisi, katmanlar arasında paylaşılan tek bir modelleme projesi oluşturur.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Her katman için ayrı bir modelleme projesi kullanmak için

1. Her katman çözümünde bir modelleme projesi oluşturun.

    Bu modelde, bu katmanın gereksinimlerini ve tasarımını tanımlayan UML diyagramları bulunur. Ayrıca, iç içe geçmiş katmanları gösteren katman diyagramları da içerebilir.

    Artık her katman için bir modeliniz ve uygulama mimarisi için bir model vardır. Her model kendi çözümünde bulunur. Bu, takım üyelerinin katmanlar üzerinde aynı anda çalışmasını sağlar.

2. Mimari çözümüne her katman çözümünün modelleme projesini ekleyin. Bunu yapmak için mimari çözümünü açın. Çözüm Gezgini, çözüm düğümüne sağ tıklayın, Ekle ' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Tek bir katman çözümünde modelleme projesine (. modelproj) gidin.

    Her model artık iki çözüm halinde görünür: "giriş" çözümü ve mimari çözümü.

3. Her katmanın modelleme projesine bir katman diyagramı ekleyin. Mimari katman diyagramının bir kopyasıyla başlayın. Katman diyagramının bağımlılıkları olmayan bölümleri silebilirsiniz.

    Ayrıca, bu katmanın ayrıntılı yapısını temsil eden katman diyagramları da ekleyebilirsiniz.

    Bu diyagramlar, bu katmanda geliştirilen kodu doğrulamak için kullanılır.

4. Mimari çözümde, Visual Studio 'Yu kullanarak tüm katmanların gereksinimlerini ve tasarım modellerini düzenleyin.

    Her katman çözümünde, modele başvuran bu katman için kod geliştirin. Modeli güncelleştirmek için aynı bilgisayarı kullanmadan geliştirme yapmak için içeriğiniz varsa modeli okuyabilir ve model oluşturmaksızın Visual Studio sürümlerini kullanarak kodu geliştirebilirsiniz. Ayrıca, bu sürümlerdeki modelden kod oluşturabilirsiniz.

    Bu yöntem, aynı anda katman modellerini düzenleyen geliştiriciler tarafından hiçbir girişim olmadığını güvence altına alır.

    Ancak modeller ayrı olduğundan, yaygın kavramlara başvurmak zordur. Her modelin, diğer katmanlardan ve mimariden bağımlı olduğu öğelerin kendi kopyasına sahip olması gerekir. Her katmandaki katman diyagramının mimari katman diyagramı ile eşitlenmiş durumda tutulması gerekir. Bu öğeler değiştiğinde eşitlemenin korunması zordur, ancak bunu gerçekleştirmek için Araçlar geliştirebilirsiniz.

###### <a name="to-use-a-separate-package-for-each-layer"></a>Her katman için ayrı bir paket kullanmak için

1. Her katmanın çözümünde mimari modelleme projesini ekleyin. Çözüm Gezgini, çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Tek modelleme projesine artık her bir çözümden erişilebilir: mimari proje ve her katmanın geliştirme projesi.

2. Paylaşılan UML modelinde, her katman için bir paket oluşturun: Çözüm Gezgini, modelleme projesini seçin. UML Model Gezgini ' nde model kök düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **paket**' e tıklayın.

    Her paket, ilgili katmanın gereksinimlerini ve tasarımını tanımlayan UML diyagramları içerir.

3. Gerekirse, her bir katmanın iç yapısına yönelik yerel katman diyagramları ekleyin.

    Bu yöntem, her bir katmanın tasarım öğelerinin, bağımlı olduğu katmanlara ve ortak mimariye doğrudan başvuranlara izin verir.

    Farklı paketlerdeki eşzamanlı iş bazı çakışmalara neden olabilir, ancak paketler ayrı dosyalarda depolandığından yönetilmesi oldukça kolaydır. Önemli zorluk, bağımlı bir paketten başvurulan bir öğenin silinmesinden kaynaklanmıştır. Daha fazla bilgi için bkz. [sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md).

## <a name="creating-architecture-templates"></a>Mimari şablonları oluşturma

Uygulamada, tüm Visual Studio çözümlerinizi aynı anda oluşturmayacak, ancak proje ilerledikçe bunları Ekleriniz. Büyük olasılıkla gelecekteki projelerde aynı çözüm yapısını da kullanacaksınız.  Yeni çözümleri hızlı bir şekilde oluşturmanıza yardımcı olmak için bir çözüm veya proje şablonu oluşturabilirsiniz. Şablonu bir Visual Studio Tümleştirme Uzantısı 'nda (VSıX) yakalayıp diğer bilgisayarlara dağıtmak ve yüklemek kolay olacak şekilde yakalayabilirsiniz.

Örneğin, sunum, Iş ve veri katmanlarındaki çözümleri sıklıkla kullanıyorsanız, bu yapıya sahip yeni çözümler oluşturacak bir şablonu yapılandırabilirsiniz.

#### <a name="to-create-a-solution-template"></a>Bir çözüm şablonu oluşturmak için

1. Bunu yapmadıysanız, [şablonu dışarı aktarma Sihirbazı 'Nı indirin ve yükleyin](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Gelecekteki projeler için başlangıç noktası olarak kullanmak istediğiniz çözüm yapısını oluşturun.

3. **Dosya** menüsünde, **Şablonu VSIX olarak dışarı aktar**' a tıklayın. **Şablonu VSIX olarak dışarı Aktar Sihirbazı** açılır.

4. Sihirbazdaki yönergeleri izleyerek, şablona dahil etmek istediğiniz projeleri seçin, şablon için bir ad ve açıklama girin ve bir çıkış konumu belirtin.

> [!NOTE]
> Bu konudaki malzeme, en değerli uzmanlar (MVP), Microsoft Hizmetleri ve Visual Studio arasında işbirliği olan Visual Studio ALM derecelendirmeleri tarafından yazılmış, Visual Studio mimari araç kılavuzlarından ve paraphrased soyutlanmaktadır. ürün ekibi ve yazıcılar. [Tüm rehberlik paketini indirmek için buraya tıklayın.](https://archive.codeplex.com/?p=vsarchitectureguide)

## <a name="related-materials"></a>İlgili malzemeler

[Modellerinizi organize etme ve yönetme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models) -Clint Edmondson 'a göre video.

[Visual Studio mimarisi araç Kılavuzu](../modeling/visual-studio-architecture-tooling-guidance.md) – bir takımda modelleri yönetme hakkında daha fazla rehberlik

## <a name="see-also"></a>Ayrıca Bkz.

[Sürüm denetimi altındaki modelleri ve diyagramları yönetin](../modeling/manage-models-and-diagrams-under-version-control.md)
[geliştirme sürecinizdeki modelleri kullanın](../modeling/use-models-in-your-development-process.md)
