---
title: Modelleme çözümünüzün yapısını oluşturma
description: Uygulamayı genel katman diyagramında yer alan katmanlara karşılık gelen farklı parçalara bölmeye ilişkin bir modelleme şeması öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 1e58bd037b699b4dcb4fc5eef15c11fa2567b7a6
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517791"
---
# <a name="structure-your-modeling-solution"></a>Modelleme çözümünüzün yapısını oluşturma

Bir geliştirme projesinde modelleri etkili bir şekilde kullanmak için ekip üyelerinin projenin farklı bölümlerinin modelleri üzerinde aynı anda çalışabilecek olması gerekir. Bu konu, uygulamayı genel katman diyagramında yer alan katmanlara karşılık gelen farklı parçalara bölmeye ilişkin bir düzen önerir.

Bir projeyi veya alt projeyi hızla başlatmak için, seçtiğiniz proje yapısını izleyen bir proje şablonuna sahip olmak yararlıdır. Bu konu başlığında, böyle bir şablonun nasıl oluşturularak kullanılası açıklanmıştır.

Bu konu başlığında, birkaç ekip üyesi gerektirecek kadar büyük bir proje üzerinde çalıştığın ve belki de birkaç ekibin olduğu varsayıldı. Projenin kodu ve modelleri gibi bir kaynak denetim sisteminde [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] depolanır. En azından bazı ekip üyeleri Visual Studio geliştirmek için bu modeli kullanır ve diğer ekip üyeleri modelleri diğer Visual Studio sınar.

Her araç ve modelleme özelliğini Visual Studio sürümlerini görmek için bkz. Mimari ve modelleme [araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="solution-structure"></a>Çözüm yapısı

Orta veya büyük bir projede ekibin yapısı uygulamanın yapısına dayalıdır. Her ekip bir Visual Studio kullanır.

### <a name="to-divide-an-application-into-layers"></a>Bir uygulamayı katmanlara bölmek için

1. Çözümlerinizin yapısını web uygulaması, hizmet uygulaması veya masaüstü uygulaması gibi uygulamanın yapısına göre temel edin. Çeşitli ortak mimariler, Microsoft Uygulama Mimarisi [Kılavuzu'daki Uygulama Mimari türleri'nde ele alınmıştır.](/previous-versions/msp-n-p/ee658107(v=pandp.10))

2. Mimari Visual Studio çağırarak bir çözüm oluşturun. Bu çözüm, sistemin genel tasarımını oluşturmak için kullanılacaktır. Modeller içerir ancak kod içermez.

   Bu çözüme bir bağımlılık diyagramı ekleyin. Bağımlılık diyagramında, uygulama için seçtiğiniz mimariyi çizin. Örneğin, diyagram bu katmanları ve aralarındaki bağımlılıkları gösterebilir: Sunum; İş mantığı; ve Veri.

4. Mimari bağımlılık Visual Studio her katman için ayrı bir çözüm oluşturun.

   Bu çözümler, katmanların kodunu geliştirmek için kullanılacaktır.

5. Katmanların tasarımlarını ve tüm katmanlar için ortak olan kavramları temsil eden modeller oluşturun. Modelleri, mimari çözümünden tüm modellerin ve ilgili modellerin her katmandan görüle bir şekilde düzenleyebilirsiniz.

   Bunu aşağıdaki yordamlardan birini kullanarak yapabilirsiniz. İlk alternatif, her katman için ayrı bir modelleme projesi, ikincisi ise katmanlar arasında paylaşılan tek bir modelleme projesi oluşturur.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Her katman için ayrı bir modelleme projesi kullanma

1. Her katman çözümünde bir modelleme projesi oluşturun.

   Bu model, bu katmanın gereksinimlerini ve tasarımını açıklayan diyagramlar içerir. İç içe geçmiş katmanların gösterildiği bağımlılık diyagramları da içerebilir.

   Artık her katman için bir modelin yanı sıra uygulama mimarisi için bir modele sahipsiniz. Her model kendi çözümünde yer alan bir modeldir. Bu, ekip üyelerinin katmanlar üzerinde aynı anda çalışmasına olanak sağlar.

2. Mimari çözümüne her katman çözümünün modelleme projesini ekleyin. Bunu yapmak için Mimari çözümünü açın. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın, Ekle'nin üzerine gelin ve ardından Var olan **Project.** Tek katman çözümünde modelleme projesine (.modelproj) gidin.

   Her model artık iki çözümde görünür: "ana" çözümü ve Mimari çözümü.

3. Her katmanın modelleme projesine bir bağımlılık diyagramı ekleyin. Mimari bağımlılık diyagramının bir kopyasıyla başlama. Bağımlılık diyagramının bağımlılıkları olan bölümleri silebilirsiniz.

   Bu katmanın ayrıntılı yapısını temsil eden bağımlılık diyagramları da ekebilirsiniz.

   Bu diyagramlar, bu katmanda geliştirilen kodu doğrulamak için kullanılır.

4. Mimari çözümünde, tüm katmanların gereksinimlerini ve tasarım modellerini düzenlemek için Visual Studio.

   Her katman çözümünde, modele başvuran bu katman için kodu geliştirin. Modeli güncelleştirmek için aynı bilgisayarı kullanmadan geliştirmeyi yapmak için içerik kullanıyorsanız, modeli okuyabilir ve model oluşturamazsınız Visual Studio sürümlerini kullanarak kod geliştirebilirsiniz. Ayrıca bu sürümlerde modelden kod da üretebilirsiniz.

   Bu yöntem, katman modellerini aynı anda düzende bulunduran geliştiricilerin müdahaleye neden olacağını garanti eder.

   Ancak modeller ayrı olduğundan genel kavramlara başvurmak zordur. Her modelin, diğer katmanlara ve mimariye bağımlı olduğu öğelerin kendi kopyasına sahip olması gerekir. Her katmanda bağımlılık diyagramı, Mimari bağımlılık diyagramı ile eşit tutulmalıdır. Bu öğeler değişirken eşitlemeyi sürdürmek zordur, ancak bunu gerçekleştirmek için araçlar geliştirebilirsiniz.

#### <a name="use-a-separate-package-for-each-layer"></a>Her katman için ayrı bir paket kullanma

1. Her katmanın çözümünde Mimari modelleme projesini ekleyin. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Mevcut **Uygulama'Project.** Tek modelleme projesine artık her çözümden erişilebilir: Mimari projesi ve her katman için geliştirme projesi.

2. Paylaşılan modelde her katman için bir paket oluşturun: Çözüm Gezgini **projesini** seçin. **UML Model Gezgini'nde,** model kök düğümüne sağ tıklayın, Ekle'nin üzerine **gelin ve** ardından Paketle'ye **tıklayın.**

   Her paket, ilgili katmanın gereksinimlerini ve tasarımını açıklayan diyagramlar içerir.

3. Gerekirse, her katmanın iç yapısı için yerel bağımlılık diyagramları ekleyin.

   Bu yöntem, her bir katmanın tasarım öğelerinin, bağlı olduğu katmanlara ve ortak mimariye doğrudan başvurur.

   Farklı paketlerde eşzamanlı çalışma bazı çakışmalara neden olsa da, paketler ayrı dosyalarda depolandığı için bunların yönetimi oldukça kolaydır.

## <a name="create-architecture-templates"></a>Mimari şablonları oluşturma

Uygulamada, tüm çözümlerinizi aynı anda Visual Studio proje ilerledikçe bunları eklersiniz. Muhtemelen gelecekteki projelerde de aynı çözüm yapısını kullanacağız. Yeni çözümleri hızlı bir şekilde oluşturmanıza yardımcı olmak için bir çözüm veya proje şablonu oluşturabilirsiniz. Şablonu, diğer bilgisayarlara Visual Studio ve yüklemesi kolay olacak şekilde bir Visual Studio Tümleştirme Uzantısı'nın (VSIX) içinde yakaabilirsiniz.

Örneğin, Sunu, İş ve Veri katmanlarına sahip çözümleri sık sık kullanıyorsanız, bu yapıya sahip yeni çözümler oluşturacak bir şablon yapılandırabilirsiniz.

### <a name="to-create-a-solution-template"></a>Çözüm şablonu oluşturmak için

1. [Şablonu Dışarı Aktarma Sihirbazı'nı indirin ve yükleyin.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard)

2. Gelecekteki projeler için başlangıç noktası olarak kullanmak istediğiniz çözüm yapısını oluşturun.

3. Dosya menüsünde **Şablonu** **VSIX Olarak Dışarı Aktar'a tıklayın.**

   **ŞABLONU VSIX Olarak Dışarı Aktarma Sihirbazı** açılır.

4. Sihirbazda verilen yönergeleri izleyerek, şablona eklemek istediğiniz projeleri seçin, şablon için bir ad ve açıklama girin ve bir çıkış konumu belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
