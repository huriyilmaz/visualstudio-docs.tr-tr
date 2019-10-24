---
title: Modelleme çözümünüzün yapısını oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73a1c6458bf6afc5d6fce34208dd8c2c3ddda37f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748211"
---
# <a name="structure-your-modeling-solution"></a>Modelleme çözümünüzün yapısını oluşturma

Bir geliştirme projesinde modelleri etkin bir şekilde kullanmak için, takım üyelerinin projenin farklı bölümlerinin modelleriyle aynı anda çalışabilebilmesi gerekir. Bu konu başlığı altında, uygulamayı genel bir katman diyagramındaki katmanlara karşılık gelen farklı bölümlere bölmek için bir düzen önerilir.

Bir projede veya alt projede hızlı bir şekilde başlamak için, seçtiğiniz proje yapısını izleyen bir proje şablonu olması yararlı olur. Bu konu, böyle bir şablonun nasıl oluşturulacağını ve kullanılacağını açıklar.

Bu konu, birkaç takım üyesi gerektirecek kadar büyük bir proje üzerinde çalıştığınızı ve belki de birçok takıma sahip olduğunu varsayar. Projenin kodu ve modelleri [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] gibi bir kaynak denetimi sisteminde depolanır. En az bazı takım üyeleri, model geliştirmek için Visual Studio kullanır ve diğer takım üyeleri diğer Visual Studio sürümlerini kullanarak modelleri görüntüleyebilir.

Hangi Visual Studio sürümlerinin her bir aracı ve modelleme özelliğini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Çözüm yapısı

Orta veya büyük bir projede, ekibin yapısı uygulamanın yapısına göre belirlenir. Her takım bir Visual Studio çözümü kullanır.

### <a name="to-divide-an-application-into-layers"></a>Bir uygulamayı katmanlara bölmek için

1. Web uygulaması, hizmet uygulaması veya masaüstü uygulaması gibi, çözümünüzün yapısını uygulamanızın yapısına dayandırın. Birçok yaygın [mimaride, Microsoft uygulama mimarisi Kılavuzu 'Ndaki uygulama arşiv türleri](http://go.microsoft.com/fwlink/?LinkId=196681)bölümünde açıklanmaktadır.

2. Mimari çözümünü çağıracağımız bir Visual Studio çözümü oluşturun. Bu çözüm, sistemin genel tasarımını oluşturmak için kullanılacaktır. Modeller içerir, ancak kod içermez.

   Bu çözüme bir bağımlılık diyagramı ekleyin. Bağımlılık diyagramında, uygulamanız için seçtiğiniz mimariyi çizin. Örneğin, diyagram bu katmanları ve bunlar arasındaki bağımlılıkları gösterebilir: sunum; İş mantığı; ve verileri.

4. Mimari bağımlılık diyagramında her katman için ayrı bir Visual Studio çözümü oluşturun.

   Bu çözümler katmanların kodunu geliştirmek için kullanılacaktır.

5. Katmanların ve tüm katmanlarda ortak olan kavramların tasarımlarını temsil eden modeller oluşturun. Tüm modellerin mimari çözümden görünebilmesi ve ilgili modellerin her katmandan görünebilmesi için modelleri düzenleyin.

   Bunu, aşağıdaki yordamlardan birini kullanarak elde edebilirsiniz. İlk alternatif, her katman için ayrı bir modelleme projesi oluşturur ve ikincisi, katmanlar arasında paylaşılan tek bir modelleme projesi oluşturur.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Her katman için ayrı bir modelleme projesi kullanın

1. Her katman çözümünde bir modelleme projesi oluşturun.

   Bu modelde, bu katmanın gereksinimlerini ve tasarımını tanımlayan diyagramlar bulunur. Ayrıca, iç içe geçmiş katmanları gösteren bağımlılık diyagramları da içerebilir.

   Artık her katman için bir modeliniz ve uygulama mimarisi için bir model vardır. Her model kendi çözümünde bulunur. Bu, takım üyelerinin katmanlar üzerinde aynı anda çalışmasını sağlar.

2. Mimari çözümüne her katman çözümünün modelleme projesini ekleyin. Bunu yapmak için mimari çözümünü açın. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, Ekle ' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Tek bir katman çözümünde modelleme projesine (. modelproj) gidin.

   Her model artık iki çözüm halinde görünür: "giriş" çözümü ve mimari çözümü.

3. Her katmanın modelleme projesine bir bağımlılık diyagramı ekleyin. Mimari bağımlılık diyagramının bir kopyasıyla başlayın. Bağımlılık diyagramının bağımlılıkları olmayan bölümleri silebilirsiniz.

   Ayrıca, bu katmanın ayrıntılı yapısını temsil eden bağımlılık diyagramları da ekleyebilirsiniz.

   Bu diyagramlar, bu katmanda geliştirilen kodu doğrulamak için kullanılır.

4. Mimari çözümde, Visual Studio 'Yu kullanarak tüm katmanların gereksinimlerini ve tasarım modellerini düzenleyin.

   Her katman çözümünde, modele başvuran bu katman için kod geliştirin. Modeli güncelleştirmek için aynı bilgisayarı kullanmadan geliştirme yapmak için içeriğiniz varsa modeli okuyabilir ve model oluşturmaksızın Visual Studio sürümlerini kullanarak kodu geliştirebilirsiniz. Ayrıca, bu sürümlerdeki modelden kod oluşturabilirsiniz.

   Bu yöntem, aynı anda katman modellerini düzenleyen geliştiriciler tarafından hiçbir girişim olmadığını güvence altına alır.

   Ancak modeller ayrı olduğundan, yaygın kavramlara başvurmak zordur. Her modelin, diğer katmanlardan ve mimariden bağımlı olduğu öğelerin kendi kopyasına sahip olması gerekir. Her katmandaki bağımlılık diyagramı, mimari bağımlılık diyagramı ile eşitlenmiş durumda tutulmalıdır. Bu öğeler değiştiğinde eşitlemenin korunması zordur, ancak bunu gerçekleştirmek için Araçlar geliştirebilirsiniz.

#### <a name="use-a-separate-package-for-each-layer"></a>Her katman için ayrı bir paket kullanın

1. Her katmanın çözümünde mimari modelleme projesini ekleyin. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Tek modelleme projesine artık her bir çözümden erişilebilir: mimari proje ve her katmanın geliştirme projesi.

2. Paylaşılan modelde, her katman için bir paket oluşturun: **Çözüm Gezgini**, modelleme projesini seçin. **UML Model Gezgini**' nde model kök düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **paket**' e tıklayın.

   Her pakette, ilgili katmanın gereksinimlerini ve tasarımını tanımlayan diyagramlar bulunur.

3. Gerekirse, her bir katmanın iç yapısına yönelik yerel bağımlılık diyagramları ekleyin.

   Bu yöntem, her bir katmanın tasarım öğelerinin, bağımlı olduğu katmanlara ve ortak mimariye doğrudan başvuranlara izin verir.

   Farklı paketlerdeki eşzamanlı iş bazı çakışmalara neden olabilir, ancak paketler ayrı dosyalarda depolandığından yönetilmesi oldukça kolaydır.

## <a name="create-architecture-templates"></a>Mimari şablonları oluşturma

Uygulamada, tüm Visual Studio çözümlerinizi aynı anda oluşturmaz, ancak proje ilerledikçe ekleyin. Ayrıca, gelecekteki projelerde aynı çözüm yapısını da kullanacaksınız. Yeni çözümleri hızlı bir şekilde oluşturmanıza yardımcı olmak için bir çözüm veya proje şablonu oluşturabilirsiniz. Şablonu bir Visual Studio Tümleştirme Uzantısı 'nda (VSıX) yakalayıp diğer bilgisayarlara dağıtmak ve yüklemek kolay olacak şekilde yakalayabilirsiniz.

Örneğin, sunum, Iş ve veri katmanlarındaki çözümleri sıklıkla kullanıyorsanız, bu yapıya sahip yeni çözümler oluşturacak bir şablonu yapılandırabilirsiniz.

### <a name="to-create-a-solution-template"></a>Bir çözüm şablonu oluşturmak için

1. [Şablonu dışarı aktarma sihirbazını indirin ve yükleyin](http://go.microsoft.com/fwlink/?LinkId=196686).

2. Gelecekteki projeler için başlangıç noktası olarak kullanmak istediğiniz çözüm yapısını oluşturun.

3. **Dosya** menüsünde, **Şablonu VSIX olarak dışarı aktar**' a tıklayın.

   **Şablonu VSIX olarak dışarı Aktar Sihirbazı** açılır.

4. Sihirbazdaki yönergeleri izleyerek, şablona dahil etmek istediğiniz projeleri seçin, şablon için bir ad ve açıklama girin ve bir çıkış konumu belirtin.

## <a name="watch-a-video"></a>Video izleyin

[Modellerinizi düzenleyin ve yönetin](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Visual Studio Mimari Araç Kullanımı Kılavuzu](../modeling/visual-studio-architecture-tooling-guidance.md)
