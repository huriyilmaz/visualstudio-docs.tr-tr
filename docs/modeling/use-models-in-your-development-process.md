---
title: Geliştirme sürecinizde modelleri kullanma
description: Bu Visual Studio, bir sistemi, uygulamayı veya bileşeni anlamanıza ve değiştirmeye yardımcı olmak için bir model kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 910aa4d25325ac6498e941bbba3a1a6d7ee2f957
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637254"
---
# <a name="use-models-in-your-development-process"></a>Geliştirme sürecinizde modelleri kullanma

Bu Visual Studio, bir sistemi, uygulamayı veya bileşeni anlamanıza ve değiştirmeye yardımcı olmak için bir model kullanabilirsiniz. Bir model, sisteminizin çalışma dünyasına görselleştirmenize, kullanıcıların ihtiyaçlarını netleştirmenize, sisteminizin mimarisini tanımlamanıza, kodu analiz etmenize ve kodunuzun gereksinimleri karşılamasına yardımcı olabilir. Bkz. [Channel 9 Video: Modelleme ile mimariyi geliştirme.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)

Her model türünü destekleyen Visual Studio sürümlerini görmek için [bkz. Mimari ve](../modeling/analyze-and-model-your-architecture.md#VersionSupport)modelleme araçları için sürüm desteği.

Modeller çeşitli yollarla size yardımcı olabilir:

- Modelleme diyagramları çizmek gereksinimler, mimari ve üst düzey tasarımla ilgili kavramları netleştirmeye yardımcı olur. Daha fazla bilgi için [bkz. Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

- Modellerle çalışmak, gereksinimlerde tutarsızlıkları ortaya çıkarmanıza yardımcı olabilir.

- Modellerle iletişim kurmak, önemli kavramları doğal dilden daha az belirsiz bir şekilde iletişim kurmanıza yardımcı olur. Daha fazla bilgi için [bkz. Uygulama mimarinizi modelleme.](../modeling/model-your-app-s-architecture.md)

- Bazen kod veya veritabanı şemaları ya da belgeler gibi diğer yapıtlar oluşturmak için modelleri kullanabilirsiniz. Örneğin, bir modelin Visual Studio bileşenleri bir modelden oluşturulur. Daha fazla bilgi için [bkz. Modellerden uygulama oluşturma ve yapılandırma.](../modeling/generate-and-configure-your-app-from-models.md)

Modelleri, aşırı çevikten yüksek sremoniye kadar çok çeşitli işlemlerde kullanabilirsiniz.

## <a name="use-models-to-reduce-ambiguity"></a>Belirsizlikleri azaltmak için modelleri kullanma

Modelleme dili, doğal dilden daha az belirsizdir ve yazılım geliştirme sırasında genellikle gerekli olan fikirleri ifade etmek için tasarlanmıştır.

Projenizin çevik uygulamaları takip eden küçük bir takımı varsa, kullanıcı hikayelerini netleştirmenize yardımcı olmak için modelleri kullanabilirsiniz. Müşteriyle ihtiyaçlarıyla ilgili tartışmalarda, model oluşturmak ani veya prototip kod yazmaktan çok daha hızlı ve ürünün daha geniş bir alanında yararlı sorular üretebilirsiniz.

Projeniz büyükse ve dünyanın farklı yerlerinde ekipler bulunuyorsa, gereksinimleri ve mimariyi düz metinden çok daha etkili bir şekilde iletişim kurmanıza yardımcı olması için modelleri kullanabilirsiniz.

Her iki durumda da model oluşturmak neredeyse her zaman tutarsızlıklarda ve belirsizliklerde önemli bir azalmaya neden olur. Farklı proje katılımcıları genellikle sistemin iş dünyasındaki farklı anlayışlarına sahip olur ve farklı geliştiriciler sistemin nasıl çalıştığını sık sık anlar. Bir modeli tartışma odağı olarak kullanmak genellikle bu farkları ortaya çıkarır. Tutarsızlıkları azaltmak için model kullanma hakkında daha fazla bilgi için bkz. [Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

## <a name="use-models-with-other-artifacts"></a>Modelleri diğer yapıtlarla kullanma

Model tek başına bir gereksinimler belirtimi veya mimarisi değildir. Bu, bunların bazı yönlerini daha net bir şekilde ifade etmek için bir araçtır, ancak yazılım tasarımı sırasında gerekli olan tüm kavramlar ifade etmek değildir. Bu nedenle modeller, Team Foundation'daki OneNote sayfaları veya paragrafları, Microsoft Office belgeleri, iş öğeleri veya proje odası duvarında yapışkan notlar gibi diğer iletişim araçlarıyla birlikte kullanılmalıdır. Son öğe dışında, bu nesne türlerinin hepsi modelin öğe bölümlerine bağlanabilirsiniz.

Normalde modellerle birlikte kullanılan belirtimlerin diğer yönleri şunlardır. Projenizin ölçeğine ve stiline bağlı olarak, bu yönlerin birkaçını kullanabilir veya hiç kullanmayamazsiniz:

- Kullanıcı hikayeleri. Kullanıcı hikayesi, kullanıcıların ve diğer proje katılımcılarının projenin yinelemelerinden biri ile teslim edilecek sistem davranışının bir yönüyle ilgili kısa bir açıklamadır. Tipik bir kullanıcı hikayesi "Müşteri bunu mümkün olacak...". Bir kullanıcı hikayesi, bir kullanım örnekleri grubu ortaya veya daha önce geliştirilmiş kullanım örnekleri uzantılarını tanımlayabilir. Kullanım örnekleri tanımlayarak veya genişleterek kullanıcı hikayesini daha net bir şekilde ifade etmek.

- İstekleri Değiştirme. Daha resmi bir projede değişiklik isteği, çevik bir proje içinde yer alan kullanıcı hikayesine çok benzer. Çevik yaklaşım, tüm gereksinimleri önceki yinelemelerde geliştirilen değişiklikler olarak gösterir.

- Kullanım durumu açıklaması. Kullanım durumu, kullanıcının belirli bir hedefe ulaşmak için sistemle etkileşim kurduğu bir yolu temsil eder. Tam açıklama hedefi, ana ve alternatif olay dizilerini ve olağanüstü sonuçları içerir. Kullanım durumu diyagramı, kullanım örnekleri özetleme ve genel bakış sağlamada yardımcı olur.

- Senaryo. Senaryo, sistemin, kullanıcıların ve diğer sistemlerin paydaşlara değer sağlamak için birlikte nasıl çalışsa da çalışmalarını gösteren bir olay dizisinin oldukça ayrıntılı bir açıklamasıdır. Kullanıcı arabiriminin slayt gösterisi veya kullanıcı arabiriminin prototipi şeklinde olabilir. Bir kullanım durumu veya kullanım örnekleri dizisi açık olabilir.

- Sözlük. Projenin gereksinimler sözlüğü, müşterilerin dünyalarını tartışacakları sözcükleri açıklar. Kullanıcı arabirimi ve gereksinimler modelleri de bu terimleri kullanlıdır. Sınıf diyagramı, bu terimlerin çoğu arasındaki ilişkilerin netleştirmeye yardımcı olabilir. Diyagramların ve sözlüklerin oluşturulması kullanıcılar ve geliştiriciler arasındaki yanlış anlamaları azaltmanın yanı sıra, farklı iş paydaşları arasındaki yanlış anlamaları da neredeyse her zaman ortaya çıkarır.

- İş kuralları. Birçok iş kuralı, gereksinimler sınıf modelinde ilişkilendirmeler ve öznitelikler üzerinde sabit kısıtlamalar olarak ve sıra diyagramlarında kısıtlamalar olarak ifade olabilir.

- Üst düzey tasarım. Ana parçaları ve bunların nasıl bir araya geldiklerini açıklar. Bileşen, dizi ve arabirim diyagramları, üst düzey tasarımın önemli bir parçasıdır.

- Tasarım desenleri. Sistemin farklı bölümleri arasında paylaşılan tasarım kurallarını açıklama.

- Test belirtimleri. Test betikleri ve test kodu tasarımları, test adımları dizilerini açıklamak için etkinlik ve sıralı diyagramlardan iyi bir şekilde kullanılabilir. Sistem testleri, gereksinimler değiştiklerinde kolayca değiştirilemeyecek şekilde gereksinimler modeli açısından ifade edilebilir.

- Project plan. Proje planı veya biriktirme listesi, her özelliğin ne zaman teslim olacağını tanımlar. Hangi kullanım durumlarını ve iş kurallarını uygulaydığını veya genişlet yaptığını belirterek her özelliği tanımlayabilirsiniz. Kullanım örneklerine ve iş kurallarına doğrudan planda başvurabilirsiniz veya ayrı bir belgede bir özellik kümesi tanımlayabilir ve planda özellik başlıklarını kullanabilirsiniz.

## <a name="use-models-in-iteration-planning"></a>Yineleme planlamada modelleri kullanma

Tüm projeler kendi ölçeğinde ve kuruluşunda farklı olsa da, tipik bir proje iki ile altı hafta arasında bir dizi yineleme olarak planlanmaktadır. Daha sonraki yinelemelerin kapsamını ve planlarını ayarlamak için erken yinelemelerden geri bildirim sağlayacak kadar yineleme planlamak önemlidir.

Aşağıdaki önerilerin, bir iterative projede modellemenin avantajlarını hayata bulmaya yardımcı olmak için yararlı olduğunu bulabilirsiniz.

### <a name="sharpen-focus-as-each-iteration-approaches"></a>Her yineleme yaklaşımında odağın netleştirmesi

Her yineleme yaklaşımında, yinelemenin sonunda nelerin teslim edilecek olduğunu tanımlamaya yardımcı olması için modelleri kullanın.

- Erken yinelemelerde her şeyi ayrıntılı olarak modellemeyin. İlk yinelemede, kullanıcı sözlüğünde ana öğeler için bir sınıf diyagramı oluşturun, ana kullanım örneklerine bir diyagram çizin ve ana bileşenlerin bir diyagramını çizin. Proje daha sonra değiştireceğimiz için bunların herhangi birini ayrıntılı olarak açıklamayın. Özelliklerin veya önemli kullanıcı hikayelerinin bir listesini oluşturmak için bu modelde tanımlanan terimleri kullanın. Proje genelinde tahmini iş yükünü yaklaşık olarak dengelemek için özellikleri yinelemelere attayın. Bu atamalar daha sonra projesinde değişecektir.

- Erken bir yinelemede tüm en önemli kullanım örneklerinden basitleştirilmiş sürümleri uygulamaya çalış. Bu kullanım durumlarını sonraki yinelemelerde genişletebilirsiniz. Bu yaklaşım, gereksinimlerde bir kusur bulma riskini azaltmaya veya projenin bu konuda herhangi bir şey yapmak için çok geç olduğu mimariye yardımcı olur.

- Her yinelemenin sonuna yakın bir yerde, sonraki yinelemede geliştirilecek gereksinimleri veya kullanıcı hikayelerini ayrıntılı olarak tanımlamak için bir gereksinimler atölyesini tutun. Hem öncelikleri hem de geliştiricileri ve sistem test edenleri belirlemek için kullanıcıları ve iş paydaşlarını davet etme. 2 haftalık yinelemenin gereksinimlerini tanımlamak için üç saat izin verme.

- Atölyenin amacı, herkesin bir sonraki yinelemenin sonunda nelerin başarılı olacağını kabul etmektir. Gereksinimleri netleştirmeye yardımcı olmak için modelleri araçlardan biri olarak kullanın. Atölyenin çıkışı bir yineleme biriktirme listesidir: yani Team Foundation'daki geliştirme görevlerinin listesi ve içinde test [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] paketleri.

- Gereksinimler atölyesinde, yalnızca geliştirme görevlerine ilişkin tahminleri belirlemenize gerek olduğu sürece tasarımı tartışın. Aksi takdirde, kullanıcıların doğrudan deneyimleyebilirsiniz sistem davranışıyla ilgili tartışmayı devam edin. Gereksinimler modelini mimari modelden ayrı tutma.

- Teknik olmayan proje katılımcıları genellikle UML diyagramlarını anlamakta sorun olmaz ve sizin rehberliğiyle.

### <a name="link-model-to-work-items"></a>Modeli iş öğelerine bağlama

Gereksinimler atölyesinde gereksinimler modelinin ayrıntılarını ayrıntılı bir şekilde inceler ve modeli geliştirme görevlerine bağlamanız gerekir. Team Foundation'daki iş öğelerini modeldeki öğelere bağarak bunu yapabiliriz.

Herhangi bir öğeyi iş öğelerine bağabilirsiniz, ancak en kullanışlı öğeler şunlardır:

- İş kurallarını veya hizmet kalitesini açıklayan açıklamalar. Daha fazla bilgi için [bkz. Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

### <a name="link-model-to-tests"></a>Modeli testlere bağlama

Kabul testlerinin tasarımına rehberlik etmek için gereksinimler modelini kullanın. Bu testleri geliştirme işlerinde eşzamanlı olarak oluşturun.

Bu teknik hakkında daha fazla bilgi edinmek için bkz. [bir modelden test geliştirme](../modeling/develop-tests-from-a-model.md).

### <a name="estimate-remaining-work"></a>Kalan işi tahmin etme

Gereksinimler modeli, her yinelemenin boyutuyla ilgili olarak projenin toplam boyutunu tahmin etmenize yardımcı olabilir. Kullanım örneklerinin ve sınıflarının sayısını ve karmaşıklığını değerlendirmek, gereken geliştirme işini tahmin etmenize yardımcı olabilir. İlk birkaç yinelemeyi tamamladıktan sonra, ele alınan gereksinimlerin ve gereksinimlerin bir karşılaştırması projenin geri kalanının maliyeti ve kapsamının yaklaşık bir ölçümünü verebilir.

Her yinelemenin sonuna yakın bir şekilde, gereksinimlerin gelecekteki yinelemelere atanmasını gözden geçirin. Kullanım durumu diyagramında bir alt sistem olarak her bir yinelemenin sonunda yazılımınızın durumunu göstermek faydalı olabilir. Tartışmalarda, bu alt sistemlerden birindeki kullanım örneklerini ve kullanım örneği uzantılarını diğerine taşıyabilirsiniz.

## <a name="levels-of-abstraction"></a>Soyutlama düzeyleri

Modeller, yazılımla ilgili olarak bir soyutlama aralığına sahiptir. En somut modeller doğrudan program kodunu temsil eder ve en soyut modeller kodda gösterilebilen veya gösterilemeyen iş kavramlarını temsil eder.

Bir model, çeşitli diyagramlar aracılığıyla görüntülenebilir. Modeller ve diyagramlar hakkında daha fazla bilgi için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

Farklı türlerde diyagram, tasarımı farklı soyutlama düzeylerinde tanımlamak için faydalıdır. Birçok diyagram türü, birden fazla düzeyde yararlıdır. Bu tablo, her diyagram türünün nasıl kullanılabileceğini gösterir.

|Tasarım düzeyi|Diyagram türleri|
|-|-|
|İş Süreci<br /><br /> Sisteminizin kullanılacağı bağlamı anlamak, kullanıcıların ne ihtiyacı olduğunu anlamanıza yardımcı olur.|-Kavramsal sınıf diyagramları, iş sürecinde kullanılan iş kavramlarını anlatmaktadır.|
|Kullanıcı gereksinimleri<br /><br /> Kullanıcılarınızın sisteminizden ihtiyacı olan tanım.|-İş kuralları ve hizmet gereksinimlerinin kalitesi ayrı belgelerde açıklanabilir.|
|Yüksek düzey tasarım<br /><br /> Sistemin genel yapısı: ana bileşenler ve bunların nasıl birlikte kullanıldığı.|-Bağımlılık diyagramları, sistemin birbirine bağlı parçalar halinde nasıl yapılandırıldığını açıklamaktadır. Mimariye bağlı olduğundan emin olmak için program kodunu bağımlılık diyagramlarına karşı doğrulayabilirsiniz.|
|Kod analizi<br /><br /> Diyagramlar koddan oluşturulabilir.|-Bağımlılık diyagramları sınıflar arasındaki bağımlılıkları gösterir. Güncelleştirilmiş kod, bir bağımlılık diyagramına göre doğrulanabilir.<br />-Sınıf diyagramları, koddaki sınıfları gösterir.|

## <a name="external-resources"></a>Dış kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Videolar**|![video MSDN 'ye bağlantı: nasıl yapılır ](../data-tools/media/playvideo.gif) [videoları: UML modellerini ve diyagramlarını oluşturma ve kullanma (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))<br /><br /> ![video kanalı 9 ' a bağlantı ](../data-tools/media/playvideo.gif) [: Visual Studio 2010 ile UML](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-1-brainstorming-a-project)<br /><br /> ![video MSDN bağlantısı ](../data-tools/media/playvideo.gif) [nasıl yapılır: UML araçları ve genişletilebilirliği (Visual Studio 2010 Ultimate)](/previous-versions/visualstudio/visual-studio-2010/dd831853(v=vs.100))|
|**Forumlar**|- [Visual Studio Görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Görselleştirme & modelleme SDK 'Sı (DSL araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Bloglar**|[Microsoft DevOps](https://devblogs.microsoft.com/devops/)|
|**Teknik makaleler ve Günlükler**|[MSDN mimari Merkezi](/previous-versions/dn630665(v=msdn.10))|

## <a name="see-also"></a>Ayrıca bkz.

- [Çevik geliştirmede modelleri kullanma](/previous-versions/ff398061(v=vs.140))
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)
- [Modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]