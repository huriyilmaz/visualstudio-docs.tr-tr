---
title: Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea3fe0027827396a49eec4c6b245a9ea59652b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114892"
---
# <a name="generate-and-configure-your-app-from-models"></a>Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
Bir modelden uygulamanızın parçalarını oluşturabilir veya yapılandırabilirsiniz.

 Model, gereksinimleri doğrudan koddan daha fazla temsil eder. Uygulamanın davranışını doğrudan modelden türeterek, kodu güncelleştirerek değiştirilen gereksinimlere çok daha hızlı ve güvenilir bir şekilde yanıt verebilirsiniz. Türetmenin ayarlanması için bazı ilk işler gerekli olsa da, gereksinimlerde değişiklikler veya ürünün çeşitli türevlerini yapmayı düşünüyorsanız bu yatırım döndürülür.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Bir modelden uygulamanızın kodunu oluşturma
 Kod oluşturmanın en kolay yolu, metin şablonlarını kullanmaktır. Aynı Visual Studio çözümünde, modeli tutabilmeniz için kod oluşturabilirsiniz. Daha fazla bilgi için bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)

  Bu yöntem artımlı olarak kolayca uygulanabilir. Yalnızca belirli bir durum için kullanılan bir uygulamayla başlayın ve modelin modelden farklı olmasını istediğiniz birkaç parçasını seçin. Bu bölümlerin kaynak dosyalarını metin şablonu (. tt) dosyaları olacak şekilde yeniden adlandırın. Bu noktada, kaynak. cs dosyaları şablon dosyalarından otomatik olarak oluşturulur, bu nedenle uygulama daha önce olduğu gibi çalışır.

  Ardından kodun bir bölümünü alabilir ve bunu, modeli okuyan ve kaynak dosyanın bir bölümünü oluşturan bir metin şablonu ifadesiyle değiştirebilirsiniz. Bir modelin en az bir değeri özgün kaynağı üretmelidir, böylece uygulamayı çalıştırabilirsiniz ve daha önce olduğu gibi çalışır. Farklı model değerlerini test ettikten sonra, kodun başka bir bölümünde şablon ifadeleri eklemek için üzerine geçebilirsiniz.

  Bu artımlı yöntemi, kod oluşturmanın genellikle düşük riskli bir yaklaşım olduğu anlamına gelir. Elde edilen uygulamalar genellikle neredeyse ve el ile yazılmış bir sürüm olarak gerçekleştirilir.

  Ancak, var olan bir uygulamayla başlatırsanız, model tarafından yönetilen farklı davranışları birbirinden bağımsız olarak farklılaştırabilmeleri için ayırmak üzere çok sayıda yeniden düzenleme gerektiğini fark edebilirsiniz. Projenizin maliyetini tahmin ettiğinizde uygulamanın bu yönünü değerlendirmenizi öneririz.

## <a name="configuring-your-application-from-a-model"></a>Uygulamanızı bir modelden yapılandırma
 Çalışma zamanında uygulamanızın davranışını değiştirmek istiyorsanız, uygulama derlenmesinden önce kaynak kodu oluşturan kod oluşturmayı kullanamazsınız. Bunun yerine, modeli okumak ve davranışını uygun şekilde değiştirmek için uygulamanızı tasarlayabiliyor olabilirsiniz. Daha fazla bilgi için bkz.

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Bu yöntem artımlı olarak da uygulanabilir, ancak başlangıçta daha fazla iş vardır. Modeli okuyacak kodu yazmanız ve değerlerine değişken parçalar tarafından erişilebilmesini sağlayan bir çerçeve ayarlamanız gerekir. Değişken parçalarının genel olması kod oluşturmadan daha pahalıdır.

  Genel bir uygulama, genellikle belirli karşılıklarından daha az iyi çalışır. Performans önemli ise, proje planınız bu riskin değerlendirmesini içermelidir.

## <a name="developing-a-derived-application"></a>Türetilmiş bir uygulama geliştirme
 Aşağıdaki genel yönergeleri yararlı bulabilirsiniz.

- **Belirli bir başlangıç yapın ve ardından genelleştirin.** Önce uygulamanızın belirli bir sürümünü yazın. Bu sürüm, bir dizi koşula göre çalışmalıdır. Doğru çalıştıklarından emin olduğunuzda bir modelden türetebilirsiniz. Türetilmiş parçaları kademeli olarak genişletin.

     Örneğin, bir modelde tanımlanan sayfaları sunan bir Web uygulaması tasarlayabilmeniz için, belirli bir Web sayfaları kümesine sahip bir Web sitesi tasarlayın.

- **Değişken yönlerini modelleyin.** Bir dağıtım ya da başka bir dağıtım arasında ya da gereksinimler değiştikçe zaman içinde değişiklik olacak yönleri belirler. Bunlar bir modelden türetilmesi gereken yönlerdir.

     Örneğin, Web sayfaları kümesi ve bunlar arasındaki bağlantılar değişirse, ancak sayfaların stili ve biçimi her zaman aynıysa, modelin bağlantıları açıklaması gerekir, ancak sayfaların biçimini açıklaması gerekmez.

- **Sorunları ayırın.** Değişken yönleri bağımsız alanlara bölünecekse, her alan için ayrı modeller kullanın. ModelBus kullanarak, hem modelleri hem de aralarındaki kısıtlamaları etkileyen işlemler tanımlayabilirsiniz.

     Örneğin, Web sayfaları ve sayfaların yerleşimini tanımlamak için farklı bir model arasında gezinmeyi tanımlamak üzere bir model kullanın.

- **Çözümü değil, gereksinimi modelleyin.** Modeli, Kullanıcı gereksinimlerini açıklayan şekilde tasarlayın. Bunun aksine, gösterimi uygulamanın değişken yönlerine göre tasarlamayın.

     Örneğin, Web gezinti modeli aralarındaki Web sayfalarını ve köprüleri temsil etmelidir. Web gezinti modeli, uygulamanızdaki HTML veya sınıfların parçalarını temsil etmelidir.

- **Oluşturma veya yorumlama?** Belirli bir dağıtım için gereksinimler nadiren değişiyorsa, modelden program kodu oluşturur. Gereksinimler sıklıkla değişebilir veya aynı dağıtımda birden fazla değişkenle birlikte var olabilir veya bir modeli okuyup yorumlayabilmesi için uygulamayı yazın.

     Örneğin, bir dizi farklı ve ayrı olarak yüklenen Web siteleri geliştirmek için Web sitesi modelinizi kullanırsanız, modelden sitenin kodunu oluşturmanız gerekir. Ancak modelinizi her gün değişen bir siteyi denetlemek için kullanıyorsanız, modeli okuyan bir Web sunucusu yazmak ve siteyi buna göre temsil etmek daha iyidir.

- **UML veya DSL?** UML genişletmek için stereotipleri kullanarak modelleme gösteriminizi oluşturmayı düşünün. Amaca uygun bir UML diyagramı yoksa bir DSL tanımlayın. Ancak UML 'in standart semantiğini bozmaktan kaçının.

     Örneğin, bir UML sınıf diyagramı, kutular ve okların bir koleksiyonudur; Bu gösterimle, teorik olarak herhangi bir şeyi tanımlayabilir. Ancak, bir tür kümesini açıkladığınız durumlar haricinde sınıf diyagramını kullanmanızı önermiyoruz. Örneğin, farklı Web sayfası türlerini tanımlamaya yönelik sınıf diyagramlarını uyarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
