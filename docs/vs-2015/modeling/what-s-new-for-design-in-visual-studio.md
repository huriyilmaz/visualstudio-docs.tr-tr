---
title: Tasarım için yenilikler&#39;
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302373"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Visual Studio 2015'te Visual Studio'da tasarım için yenilikler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Visual Studio'nun bu sürümü, kodu daha iyi anlamanıza ve tasarlamanıza yardımcı olacak aşağıdaki geliştirmeleri içerir.

 **Kod haritaları ve bağımlılık grafikleri**

 Visual Studio Enterprise'da, kodunuzda belirli bağımlılıkları anlamak istediğinizde, kod eşlemleri oluşturarak bunları görselleştirin. Daha sonra, kodunuzun yanında görünen haritayı kullanarak bu ilişkilerde gezinebilirsiniz. Kod haritaları, çalışırken veya kod ayıklama sırasında koddaki yerinizi izlemenize de yardımcı olabilir, böylece kodunuzu tasarımı hakkında daha fazla bilgi edinirken daha az kod okursunuz.

 Son (RTM) sürümünde, kod öğeleri ve bağlantıları için kısayol menülerini, grup içeriğinin seçilmesi, düzenlenmesi, yönetimi ve düzenini değiştirme yle ilgili bölümlere komutları gruplandırmak tarafından kullanımı çok daha kolay hale getirdik. Test projelerinin diğer projelerden farklı bir tarzda görüntülendiğine ve haritadaki öğelerin simgelerini daha uygun sürümlere güncellediğimize de dikkat edin.

 ![Seçili öğeleri yeni bir kod haritasında gösterme](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Diğer iyileştirmeler şunlardır:

- **Geliştirilmiş yukarıdan aşağıya diyagramlar.** Orta ve büyük Visual Studio çözümleri için, çözüm için daha kullanışlı bir kod eşlemleri elde etmek için artık basitleştirilmiş bir Mimari menüsünü kullanabilirsiniz. Çözümderlemeleriniz çözüm klasörlerine göre gruplandırılır, böylece bunları bağlam içinde görebilir ve çözümü yapılandırmak için sarf ettiğiniz çabadan yararlanabilirsiniz. Proje ve derleme başvurularını hemen görürsünüz ve ardından bağlantı türleri görüntülenir. Buna ek olarak, çözümünüz dışındaki montajlar daha kompakt bir şekilde gruplandırılır.

- **Test Projeleri farklı tarz ve filtre olabilir.** Artık test projelerini harita üzerinde daha kolay ve hızlı bir şekilde tanımlayabilirsiniz, çünkü bunlar farklı şekilde şekillendirilmiştir. Uygulamanın çalışma koduna odaklanabilmeniz için filtrede de olabilir.

- **Basitleştirilmiş dış bağımlılık bağlantıları.** Bağımlılık bağlantıları artık System.Object, System.ValueType, System.Enum ve System.Delegate'den gelen kalıtımı temsil etmez ve bu da kod haritanızdaki dış bağımlılıkları görmenizi kolaylaştırır.

- **'Bağımlılık bağlantılarına giriş' filtreleri dikkate alır.** Bağımlılık bağlantısına yapılan katkıları anlamak için genişletirken kullanışlı ve net bir diyagram elde edeyim. Diyagram daha az karmaşıktır ve seçtiğiniz bağlantı filtreleme seçeneklerini dikkate alır.

- **Kod öğeleri bağlamları ile bir kod eşlemi eklenir.** Diyagramlar artık bağlamlarıyla (gerekirse filtreuygulayabileceğiniz derleme ve çözüm klasörüne kadar) göründüğünden, Çözüm Gezgini, Sınıf Görünümü, Nesne Tarayıcısı'ndan kod öğelerini sürükleyip bırakırken daha kullanışlı diyagramlar elde elabilirsiniz; veya Solution Explorer'daki öğeleri seçerken ve Kod Haritasında Göster'i seçerken.

- **Reaktif kod eşlemlerini daha hızlı alın.** Sürükle ve bırak işlemleri hemen bir sonuç üretir ve düğümler arasındaki bağlantılar, bir düğümü genişletme veya daha fazla düğüm isteme gibi sonraki kullanıcı tarafından başlatılan işlemleri etkilemeden çok daha hızlı bir şekilde oluşturulur. Çözümü oluşturmadan kod eşlemleri oluşturduğunuzda, derlemeler oluşturulmamagibi tüm köşe örnekleri artık işlenir.

- **Çözümünüzü yeniden oluşturmayı atlayın.** Diyagramlar oluştururken ve düzenlerken daha iyi performans sağlar.

- **Filtre kodu öğesi düğümleri ve grupları**. Kod öğelerini kendi kategorilerine göre göstererek veya gizleyerek ve kod öğelerini çözüm klasörlerine, derlemelere, ad alanlarına, proje klasörlerine ve türlerine göre gruplandırarak haritalarınızı hızla dağınıklayabilirsiniz.

- **Diyagramların okunmasını kolaylaştırmak için ilişkileri filtreleyin.** Bağlantı filtreleme artık çapraz grup bağlantıları için de geçerlidir, bu da filtre penceresiyle çalışmayı önceki sürümlere göre daha az müdahaleci yapar.

- **Sınıf Görünümü ve Nesne Tarayıcısından diyagramlar oluşturun.** Sınıf Görünümü ve Nesne Tarayıcısı pencerelerinden dosyaları ve derlemeleri yeni veya varolan bir haritaya sürükleyin ve bırakın.

  Çözümlerinizde [Harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md)bakın.

  **Bu sürümdeki diğer tasarım ve modelleme değişiklikleri:**

- **Katman diyagramları.** Bu diyagramları Sınıf Görünümü ve Nesne Tarayıcısı'nı kullanarak güncelleştirin. Yazılım tasarım gereksinimlerini karşılamak için, yazılımınız için istenen bağımlılıkları açıklamak için katman diyagramları kullanın. Bu kısıtlamaları karşılamayan kod bularak ve gelecekteki kodu bu taban çizgisiyle doğrulayarak kodu bu tasarımla tutarlı tutun.

- **UML diyagramları**. Artık koddan UML sınıf diyagramları ve sıralı diyagramlar oluşturamaz. Ama yine de yeni UML öğeleri kullanarak bu diyagramları oluşturun.

- **Mimari Explorer**. Diyagramlar oluşturmak için mimari gezgini artık kullanamazsınız. Ancak Çözüm Gezgini'ni kullanmaya devam edebilirsiniz.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a>Mimari ve modelleme araçları için sürüm desteği

Visual Studio 2015 çeşitli sürümleri mevcuttur. Bunların hepsi mimari ve modelleme araçları için destek sağlamaz. Aşağıdaki tablo, her aracın kullanılabilirliğini gösterir.

|**Özellik**|**Enterprise**|**Professional**|**Topluluk**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Kod haritaları**|Evet|Yalnızca kod eşlemlerini okumayı ve filtrelemeyi, yeni genel düğümler eklemeyi ve seçimden yeni bir Yönlendirilmiş Grafik oluşturmayı destekler.|-|-|
|**UML Sınıf diyagramları**|Evet|-|-|-|
|**UML Sıra diyagramları**|Evet|-|-|-|
|**UML Kullanım Örneği diyagramları**|Evet|-|-|-|
|**UML Etkinlik diyagramları**|Evet|-|-|-|
|**UML Bileşen diyagramları**|Evet|-|-|-|
|**Katman diyagramları**|Evet|-|-|-|
|**Yönlendirilmiş Grafikler** (DGML diyagramları)|Evet|Evet|-|-|
|**Kod klon**|Evet|-|-|-|