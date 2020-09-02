---
title: Tasarım için ne&#39;yenidir
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c68db12f8ecea523327250fec1f600639a2f267
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315336"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Visual Studio 2015 ' de Visual Studio 'daki tasarımdaki yenilikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio 'nun bu sürümü, kodu daha iyi anlamanıza ve tasarlamanıza yardımcı olması için aşağıdaki geliştirmeleri içerir.

 **Kod haritaları ve bağımlılık grafikleri**

 Visual Studio Enterprise, kodunuzda belirli bağımlılıkları anlamak istediğinizde kod haritaları oluşturarak bunları görselleştirin. Daha sonra, kodunuzun yanında görüntülenen Haritayı kullanarak bu ilişkilere gidebilirsiniz. Kod haritaları, kod çalışırken veya hata ayıkladığınızda koddaki yerinizi izlemenize yardımcı olabilir, bu nedenle kodunuzun tasarımı hakkında daha fazla bilgi edinirken daha az kod okuyacaksınız.

 Son (RTM) sürümünde, komutları seçme, düzenleme, yönetme ve grup içeriklerinin yerleşimini değiştirme ile ilgili bölümlere gruplandırarak, kod öğeleri ve bağlantılarının kısayol menülerini kullanımı çok daha kolay hale aldık. Ayrıca, test projelerinin diğer projelerden farklı bir stilde görüntülendiğine ve haritadaki öğelerin simgelerini daha uygun sürümlere güncelleştirdiğine dikkat edin.

 ![Seçili öğeleri yeni kod haritasında göster](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Diğer iyileştirmeler şunlardır:

- **İyileştirilmiş yukarıdan aşağı diyagramlar**. Orta ila büyük Visual Studio çözümleri için artık çözümünüze yönelik daha kullanışlı bir kod Haritası almak için basitleştirilmiş bir mimari menüsü kullanabilirsiniz. Çözümünüzün derlemeleri, çözüm klasörlerine göre gruplandırılır, böylece bunları bağlamda görebilir ve çözümü yapılandırırken yerleştirdiğiniz çabadan yararlanabilirsiniz. Proje ve derleme başvurularını hemen görürsünüz, daha sonra bağlantı türleri görüntülenir. Ayrıca, çözümünüzün dışındaki derlemeler daha kompakt bir şekilde gruplandırılır.

- **Test projeleri farklı stillenmiştir ve filtrelenebilir**. Artık farklı stillendirilmiş olduklarından, haritadaki test projelerini daha kolay ve hızlı bir şekilde tanımlayabilirsiniz. Ayrıca, uygulamanın çalışma koduna odaklanabilmeniz için filtrelenebilir.

- **Basitleştirilmiş dış bağımlılık bağlantıları**. Bağımlılık bağlantıları artık System. Object, System. ValueType, System. Enum ve System. Delegate öğesinden devralmayı temsil etmez ve bu da kod haritanızda dış bağımlılıkları görmeyi kolaylaştırır.

- **' Bağımlılık bağlantılarında detaya gitme ', filtreleri hesaba götürür**. Bir bağımlılık bağlantısına katkılarını anlamak için, bu kullanışlı bir diyagramı genişleterek yararlı bir diyagram alırsınız. Diyagram daha az dağınık ve seçtiğiniz bağlantı filtreleme seçeneklerini dikkate alır.

- **Kod öğeleri bağlamlarıyla birlikte bir kod haritasına eklenir**. Diyagramlar artık bağlamlarıyla göründüğünden (gerekirse filtreleyebileceğiniz derleme ve çözüm klasörüne kadar), Çözüm Gezgini, Sınıf Görünümü Nesne Tarayıcısı; öğesinden kod öğelerini Sürükleyip bırakırken daha kullanışlı diyagramlar alırsınız. Çözüm Gezgini öğeleri seçerken veya kod eşlemesinde göster ' i seçerken.

- **Reaktif kod haritalarını daha hızlı alın**. Sürükle ve bırak işlemleri anında sonuç verir ve düğümler arasındaki bağlantılar, düğümü genişletme veya daha fazla düğüm isteme gibi sonraki Kullanıcı tarafından başlatılan işlemleri etkilemeden çok daha hızlı bir şekilde oluşturulur. Çözüm oluşturmadan kod eşlemeleri oluşturduğunuzda, tüm köşe durumları (derlemeler derlenmediği gibi) artık işlenir.

- **Çözümünüzü yeniden oluşturmayı atlayın.** Diyagramlar oluştururken ve düzenlenirken daha iyi performans sağlar.

- **Kod öğesi düğümlerini ve gruplarını filtreleyin**. Kendi kategorilerine göre kod öğelerini göstererek veya gizleyerek ve kod öğelerini çözüm klasörlerine, derlemelere, ad alanlarına, proje klasörlerine ve türlerine göre gruplandırarak haritalarınızı hızlıca kolayca kaldırabilirsiniz.

- **Diyagramları daha kolay okunabilir hale getirmek için Ilişkileri filtreleyin**. Artık bağlantı filtrelemesi, çapraz grup bağlantıları için de geçerlidir. Bu, filtre penceresiyle birlikte çalışarak önceki sürümlerden daha az zorlanmaya neden olur.

- **Sınıf görünümü ve nesne tarayıcısı diyagram oluşturun**. Dosyaları ve derlemeleri Sınıf Görünümü ve Nesne Tarayıcısı Windows ' a yeni veya var olan bir haritaya sürükleyip bırakın.

  Bkz. [çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

  **Bu sürümdeki diğer tasarım ve modelleme değişiklikleri:**

- **Katman diyagramları**. Sınıf Görünümü ve Nesne Tarayıcısı kullanarak bu diyagramları güncelleştirin. Yazılım tasarımı gereksinimlerini karşılamak için, yazılım için istenen bağımlılıkları anlatmak üzere katman diyagramlarını kullanın. Bu kısıtlamalara uymayan kodu bularak ve sonraki kodu bu taban çizgisiyle doğrulayarak kodu bu tasarımla tutarlı tutun.

- **UML diyagramları**. Artık Koddan UML sınıf diyagramları ve sıra diyagramları oluşturamazsınız. Ancak, yeni UML öğelerini kullanarak bu diyagramları yine de oluşturabilirsiniz.

- **Mimari Gezgini**. Artık diyagramlar oluşturmak için Mimari Gezgini 'ni kullanamazsınız. Ancak Çözüm Gezgini kullanmaya devam edebilirsiniz.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a> Mimari ve modelleme araçları için sürüm desteği

Visual Studio 2015 çeşitli sürümlerde kullanılabilir. Bunların hepsi mimari ve modelleme araçları için destek sağlamaz. Aşağıdaki tabloda her aracın kullanılabilirliği gösterilmektedir.

|**Özellik**|**Kurumsal**|**Professional**|**Topluluk**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Kod eşlemeleri**|Yes|Yalnızca kod eşlemelerini okumayı ve filtrelemeyi, yeni genel düğümleri eklemeyi ve bir seçimden yeni bir yönlendirilmiş grafik oluşturmayı destekler.|-|-|
|**UML sınıf diyagramları**|Yes|-|-|-|
|**UML sıralı diyagramlar**|Yes|-|-|-|
|**UML Kullanım örneği diyagramları**|Yes|-|-|-|
|**UML etkinlik diyagramları**|Yes|-|-|-|
|**UML Bileşen diyagramları**|Yes|-|-|-|
|**Katman diyagramları**|Yes|-|-|-|
|**Yönlendirilmiş grafikler** (DGML diyagramları)|Yes|Yes|-|-|
|**Kod kopyası**|Yes|-|-|-|