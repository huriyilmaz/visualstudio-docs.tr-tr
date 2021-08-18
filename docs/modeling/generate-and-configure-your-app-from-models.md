---
title: Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
description: Modelin neyi temsil ettiğini ve bir modelden uygulama bölümlerini nasıl oluşturabilirsiniz veya yapılandırabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2eb43192ad2f33b37198679171b25aa8133fd06f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061252"
---
# <a name="generate-and-configure-your-app-from-models"></a>Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
Bir modelden uygulama bölümlerini oluşturabilirsiniz veya yapılandırabilirsiniz.

 Model, gereksinimleri koddan daha doğrudan temsil eder. Uygulamanın davranışını doğrudan modelden türeterek, değiştirilen gereksinimlere kodu güncelleştirmeye göre çok daha hızlı ve güvenilir bir şekilde yanıt veebilirsiniz. Türetme için bazı başlangıç çalışmaları gerekli olsa da, gereksinimlerde değişiklik bekliyorsanız veya ürünün çeşitli çeşitlerini yapmayı planlıyorsanız bu yatırım döndürülür.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Modelden Uygulama Kodunuzu Oluşturma
 Kod oluşturmanın en kolay yolu metin şablonlarını kullanmaktır. Modeli bulundurarak aynı Visual Studio çözümde kod oluşturabilirsiniz. Daha fazla bilgi için bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)

  Bu yöntemi artımlı olarak uygulamak kolaydır. Yalnızca belirli bir durum için çalışan bir uygulamayla çalışmaya başlama ve modelden farklı olmak istediğiniz birkaç parça seçin. Bu bölümlerin kaynak dosyalarını metin şablonu (.tt) dosyaları olacak şekilde yeniden adlandırabilirsiniz. Bu noktada, kaynak .cs dosyaları şablon dosyalarından otomatik olarak oluşturulur, böylece uygulama daha önce olduğu gibi çalışır.

  Ardından kodun bir kısmını alıp modeli okuyarak kaynak dosyanın bu kısmını oluşturan bir metin şablonu ifadesiyle değiştirebilirsiniz. Uygulamayı yeniden çalıştırarak daha önce olduğu gibi çalışması için modelin en az bir değeri özgün kaynağı oluşturmalıdır. Farklı model değerlerini test ettikten sonra, kodun başka bir parçasına şablon ifadeleri eklemeye geçebilirsiniz.

  Bu artımlı yöntem, kod oluşturmanın genellikle düşük riskli bir yaklaşım olduğu anlamına gelir. Sonuçta elde edilen uygulamalar genellikle el ile yazılmış bir sürümün yanı sıra neredeyse aynı performansı da sunar.

  Ancak, mevcut bir uygulamayla başlarsanız, model tarafından yönetilen farklı davranışları birbirinden bağımsız olarak farklı olacak şekilde ayırmak için çok fazla yeniden düzenleme gerekli olduğunu fark edersiniz. Projenizin maliyetini tahmin etmek için uygulamanın bu yönünü değerlendirmenizi öneririz.

## <a name="configuring-your-application-from-a-model"></a>Modelden Uygulama Yapılandırma
 Çalışma zamanında uygulamanın davranışını farklılık gösterirse, uygulama derlenmiş önce kaynak kodu oluşturan kod oluşturma kullanılamaz. Bunun yerine, modeli okumak ve davranışını buna göre değişiklik yapmak için uygulamanızı tasarabilirsiniz. Daha fazla bilgi için bkz.

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Bu yöntem artımlı olarak da uygulanabilir, ancak başlangıçta daha fazla iş vardır. Modeli okuyacak kodu yazmanız ve değerlerinin değişken bölümleri tarafından erişilebilir olmasını sağlayan bir çerçeve ayarlamanız gerekir. Değişken parçalarını genel yapmak, kod oluşturmadan daha pahalıdır.

  Genel bir uygulama genellikle belirli karşıtlarına göre daha az iyi performans gösterir. Performans kritik önem taşıyorsa, proje planınız bu riskin bir değerlendirmesini içermeli.

## <a name="developing-a-derived-application"></a>Türetilmiş Uygulama Geliştirme
 Aşağıdaki genel yönergeleri yararlı bulabilirsiniz.

- **Belirli bir başlangıç ve ardından genelleştirme.** Önce uygulamanın belirli bir sürümünü yazın. Bu sürüm tek bir koşullar kümesinde çalışmalı. Doğru şekilde çalıştığına karar verdiyseniz, bir modelden türetilmiş bir şeyler de elde edin. Türetilen parçaları kademeli olarak genişletin.

     Örneğin, bir modelde tanımlanan sayfaları sunan bir web uygulaması tasarlamadan önce belirli bir web sayfası kümesine sahip bir web sitesi tasarlayabilirsiniz.

- **Çeşitleme yönlerini modelleme.** Bir dağıtım ve başka bir dağıtım arasında veya gereksinimler değişti olarak zaman içinde farklılık gösterecek yönleri belirleme. Bunlar bir modelden türetilen yönleridir.

     Örneğin, web sayfaları ve aralarındaki bağlantılar kümesi değişirse, ancak sayfaların stili ve biçimi her zaman aynı olursa, modelin bağlantıları açıklaması gerekir, ancak sayfaların biçimini açıklamasına gerek olmaz.

- **Ayrı endişeler.** Değişken yönleri bağımsız alanlara ayrılacaksa, her alan için ayrı modeller kullanın. ModelBus'ı kullanarak hem modelleri hem de aralarındaki kısıtlamaları etkileyen işlemler tanımlayabilirsiniz.

     Örneğin, web sayfaları arasında gezintiyi tanımlamak için bir model ve sayfaların düzenini tanımlamak için farklı bir model kullanın.

- **Çözümü değil gereksinimi modelleme.** Modeli, kullanıcı gereksinimlerini açık bir şekilde tasarlar. Buna karşılık, notaları uygulamanın değişken yönlerine göre tasarlamayın.

     Örneğin, web gezintisi modeli web sayfalarını ve aralarındaki köprüleri temsil etmeli. Web gezintisi modeli, uygulamanıza html veya sınıfların parçalarını temsil etmemektedir.

- **Oluşturma veya yorumlama** Belirli bir dağıtımın gereksinimleri nadiren değişirse, modelden program kodu üretin. Gereksinimler sık sık değişiyorsa veya aynı dağıtımda birden fazla varyantta birlikte bulunuyorsa, modeli okuyabilen ve yorumlayan bir uygulama yazarak.

     Örneğin, farklı ve ayrı olarak yüklenmiş bir dizi web sitesi geliştirmek için web sitesi modelinizi kullanırsanız, sitenin kodunu modelden oluşturabilirsiniz. Ancak her gün değişiklik yapılan bir siteyi kontrol etmek için modelinizi kullanırsınız, ardından modeli okutan ve siteyi uygun şekilde sunan bir web sunucusu yazmak daha iyi olur.

- **UML mi yoksa DSL mi?** UML'i genişletmek için stereotipleri kullanarak modelleme notasyonu oluşturmayı göz önünde bulundurarak. Amaca uyan UML diyagramı yoksa DSL tanımlayın. Ancak UML'nin standart semantiğine bozmaktan kaçının.

     Örneğin UML sınıf diyagramı bir kutu ve ok koleksiyonudur; Bu ifadeyle teoride her şeyi tanımlayabilirsiniz. Ancak sınıf diyagramını, aslında bir türler kümesine açıklamanız dışında kullanmamanız önerilir. Örneğin, farklı web sayfası türlerini açıklamak için sınıf diyagramlarını uyarabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
