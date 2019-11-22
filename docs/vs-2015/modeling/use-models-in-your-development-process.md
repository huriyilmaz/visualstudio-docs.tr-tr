---
title: Geliştirme sürecinizdeki modelleri kullanın | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, using models
ms.assetid: a33ac8fc-4ba0-4850-b71b-014dc8674e54
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d5284bb163f474d67324c395a4342ccef6f8561
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298256"
---
# <a name="use-models-in-your-development-process"></a>Geliştirme sürecinizde modelleri kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da bir sistem, uygulama veya bileşeni anlamanıza ve değiştirmenize yardımcı olması için bir model kullanabilirsiniz. Bir model sisteminizin çalıştığı dünyayı görselleştirmenize, kullanıcıların ihtiyaçlarını açıklığa kavuşturmanıza, sisteminizin mimarisini tanımlamanıza, kodu analiz etmenize ve kodunuzun gereksinimleri karşıladığından emin olmanıza yardımcı olabilir. Bkz. [Channel 9 videosu: modelleme aracılığıyla mimariyi geliştirme](https://go.microsoft.com/fwlink/?LinkID=252078).

 Hangi Visual Studio sürümlerinin her model türünü desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="how-to-use-models"></a>Modelleri kullanma
 Modeller çeşitli yollarla size yardımcı olabilir:

- Modelleme diyagramları çizme, gereksinimler, mimari ve üst düzey tasarımla ilgili kavramları açıklığa kavuşturmanıza yardımcı olur. Daha fazla bilgi için bkz. [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

- Modellerle çalışma, gereksinimlerdeki tutarsızlıkları açığa çıkarmak için yardımcı olabilir.

- Modellerle iletişim kurmak, doğal dille daha az ındexattributes önemli kavramlar iletmenize yardımcı olur. Daha fazla bilgi için bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

- Bazen, kod veya veritabanı şemaları veya belgeler gibi diğer yapıtlar oluşturmak için modelleri kullanabilirsiniz. Örneğin, [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] modelleme bileşenleri bir modelden oluşturulur.  Daha fazla bilgi için bkz. [uygulamanızı modellerden oluşturma ve yapılandırma](../modeling/generate-and-configure-your-app-from-models.md).

  Yoğun çevik ve yüksek seremlere kadar çok çeşitli işlemlerde modeller kullanabilirsiniz.

### <a name="use-models-to-reduce-ambiguity"></a>Belirsizliği azaltmak için modelleri kullanma
 Modelleme dili doğal dilden daha az belirsizdir ve yazılım geliştirme sırasında genellikle gerekli olan fikirleri ifade etmek için tasarlanmıştır.

 Projenizde çevik uygulamaları takip eden küçük bir takım varsa, kullanıcı hikayelerini açıklığa kavuşturmanıza yardımcı olması için modeller kullanabilirsiniz. Müşterilerin gereksinimlerine ilişkin tartışmalarda, bir modelin oluşturulması çok daha hızlı ve ürünün daha geniş bir alanı genelinde, ani veya prototip kodu yazmadan yararlı sorular oluşturabilir.

 Projeniz büyükse ve dünyanın farklı yerlerindeki takımları içeriyorsa, gereksinimleri ve mimariyi, düz metin içinde olmanıza kıyasla çok daha etkili bir şekilde iletmek için modeller kullanabilirsiniz.

 Her iki durumda da bir model oluşturmak, tutarsızlıklar ve belirsizlikleri açısından önemli bir azalmaya neden olur. Farklı hissedarlar genellikle sistemin çalıştığı iş dünyasının farklı yönlerini kullanır ve farklı geliştiriciler sistemin nasıl çalıştığına ilişkin farklı anlara sahiptir. Bir tartışmanın odağı olarak bir modelin kullanılması genellikle bu farklılıkları açığa çıkarır. Tutarsızlıkları azaltmak için model kullanma hakkında daha fazla bilgi için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

### <a name="use-models-with-other-artifacts"></a>Diğer yapıtlarla modeller kullanma
 Bir model, bir gereksinim belirtimi veya mimari tarafından değil. Bu nesnelerin bazı yönlerini daha net bir şekilde ifade etmek için bir araçtır, ancak yazılım tasarımı sırasında gereken kavramların hepsi ifade edilemez. Bu nedenle, modeller, OneNote sayfaları veya paragrafları, Microsoft Office belgeler, [!INCLUDE[esprfound](../includes/esprfound-md.md)]iş öğeleri veya proje odası duvarındaki yapışkan notlar gibi diğer iletişim araçları ile birlikte kullanılmalıdır. Son öğeden ayrı olarak, tüm bu nesne türleri modelin öğeler bölümlerine bağlanabilir.

 Genellikle modeller ile birlikte kullanılan belirtim diğer yönleri şunlardır. Projenizin ölçek ve tarzına bağlı olarak, bu yönlerden birkaçını kullanabilir veya hiç hiçbirini kullanamazsınız:

- Kullanıcı hikayeleri. Kullanıcı hikayesi, kullanıcıların ve diğer hissedarlarla tartışılmış olan ve projenin yinelemelerinden birinde teslim edilecek sistem davranışının bir yönü olan kısa bir açıklamadır. Tipik bir kullanıcı hikayesi "Müşteri şunları yapabilecektir...." Kullanıcı hikayesi bir grup kullanım durumu oluşturabilir veya daha önce geliştirilmiş kullanım örneklerinin uzantılarını tanımlayabilir. Kullanım örneklerinin tanımlanması veya genişletilmesi, kullanıcı hikayesinin daha net olmasına yardımcı olur.

- Değişiklik Istekleri. Daha resmi bir projedeki değişiklik isteği, çevik bir projedeki kullanıcı hikayesine çok benzer. Çevik yaklaşım, tüm gereksinimleri önceki yinelemelerde geliştirildiği değişikliklerle aynı şekilde değerlendirir.

- Kullanım örneği açıklaması. Kullanım durumu, kullanıcının belirli bir amaca ulaşmak için sistemle etkileşimde bulunduğu bir yolu temsil eder. Tam açıklama hedefi, ana ve diğer olay dizilerini ve olağanüstü sonuçları içerir. Kullanım durumu diyagramı özetlemeye ve kullanım örneklerine genel bir bakış sağlamanıza yardımcı olur.

- Larla. Senaryo, sistemin, kullanıcıların ve diğer sistemlerin hissedarlara değer sağlamak için birlikte nasıl çalıştığını gösteren bir dizi olayın ayrıntılı bir açıklamasıdır. Kullanıcı arabiriminin bir slayt gösterisi veya Kullanıcı arabiriminin prototipi şeklinde olabilir. Bir kullanım durumu veya kullanım durumları dizisi tanımlayabilir.

- Sözlüğü. Projenin gereksinimler sözlüğü, müşterilerinin dünyasını tartışan kelimeleri açıklar. Kullanıcı arabirimi ve gereksinimler modelleri de bu terimleri kullanmalıdır. Bir sınıf diyagramı, bu koşulların birçoğu arasındaki ilişkilerin açıklanmasına yardımcı olabilir. Diyagram ve sözlük oluşturma, yalnızca kullanıcılar ve geliştiriciler arasındaki hatalı anlayışları azaltmaz, ancak aynı zamanda farklı iş hissedarları arasındaki hatalı anları da neredeyse her zaman gösterir.

- İş kuralları. Birçok iş kuralı, gereksinimler sınıf modelindeki ilişkilendirmeler ve özniteliklerde sabit kısıtlamalar olarak ve sıralı diyagramlarda kısıtlamalar olarak ifade edilebilir.

- Üst düzey tasarım. Ana parçaları ve bunların birbirine nasıl uyduğunu açıklar. Bileşen, dizi ve arabirim diyagramları, üst düzey bir tasarımın önemli bir parçasıdır.

- Tasarım desenleri. Sistemin farklı parçaları arasında paylaşılan tasarımın kurallarını açıkla.

- Test belirtimleri. Test betikleri ve test kodu tasarımları, test adımlarının dizilerini anlatmak için etkinlik ve sıra diyagramlarından iyi bir şekilde yararlanabilirsiniz. Gereksinimler değiştiğinde kolayca değiştirilebilmeleri için sistem testlerinin, gereksinimler modeli bakımından ifade edilmesi gerekir.

- Proje planı. Proje planı veya biriktirme listesi her bir özelliğin ne zaman teslim edileceğini tanımlar. Hangi kullanım örneklerinin ve iş kurallarının uyguladığı veya genişlettiğini belirterek her bir özelliği tanımlayabilirsiniz. Doğrudan plandaki kullanım örneklerine ve iş kurallarına başvurabilir veya ayrı bir belgede bir özellikler kümesi tanımlayabilir ve plandaki Özellik başlıklarını kullanabilirsiniz.

### <a name="use-models-in-iteration-planning"></a>Yineleme planlamasında modelleri kullanma
 Tüm projeler ölçek ve kuruluşta farklı olsa da, tipik bir proje iki ila altı hafta arasında bir dizi yineleme olarak planlanmaktadır. Daha sonraki yinelemelere yönelik kapsam ve planları ayarlamak için erken yinelemeden geri bildirimde bulunmak üzere yeterli yineleme planlamanız önemlidir.

 Yinelenen bir projede modellemenin avantajlarından faydalanmasına yardımcı olmak için aşağıdaki önerileri yararlı bulabilirsiniz.

#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Her yineleme Yaklaşıtıkça odağı keskinleştirme
 Her yineleme yaklaşırsa, yinelemenin sonunda ne yapılacağını tanımlamaya yardımcı olması için modeller kullanın.

- İlk yinelemelerde her şeyi ayrıntılı olarak modellemeyin. İlk yinelemede, Kullanıcı sözlükte ana öğeler için bir sınıf diyagramı oluşturun, büyük kullanım örneklerinin bir diyagramını çizin ve ana bileşenlerin bir diyagramını çizin. Ayrıntı projede daha sonra değişeceğinden, bunların hiçbirini ayrıntılı bir şekilde açıklama olarak belirtmeyin. Özelliklerin veya büyük Kullanıcı hikayelerinin listesini oluşturmak için bu modelde tanımlanan terimleri kullanın. Projenin tamamında tahmini iş yükünü yaklaşık olarak dengelemek için yinelemelere özellikler atayın. Bu atamalar projede daha sonra değişecektir.

- İlk yinelemede en önemli kullanım örneklerinin Basitleştirilmiş sürümlerini uygulamayı deneyin. Bu kullanım örneklerini sonraki yinelemelerde genişletin. Bu yaklaşım, gereksinimlerde veya mimarideki bir kusuru bulmak için projede çok geç olması riskini azaltmaya yardımcı olur.

- Her yinelemenin sonunda, bir sonraki yinelemede geliştirilecek gereksinimleri veya kullanıcı hikayelerini ayrıntılı olarak tanımlamak için bir Requirements Workshop ' i tutun. Geliştiricilere ve sistem sınayıcılarına ve önceliklere karar veren kullanıcıları ve iş paydaşlarını davet edebilirsiniz. 2 Haftalık yineleme için gereksinimlerin tanımlanması üç saate izin verir.

- Atölyenin hedefi, herkesin bir sonraki yinelemenin sonuna kadar neler yapılacağını kabul etmesi içindir. Gereksinimleri açıklığa kavuşturmanıza yardımcı olmak için, araçlardan biri olarak modeller kullanın. Atölyenin çıktısı bir yineleme biriktirme listesidir: diğer bir deyişle, [!INCLUDE[TCMext](../includes/tcmext-md.md)][!INCLUDE[esprfound](../includes/esprfound-md.md)] ve test paketlerindeki geliştirme görevlerinin bir listesidir.

- Gereksinimler atölyesininde, geliştirme görevlerinin tahminlerini belirlemeniz için ihtiyaç duyduğunuz tasarımı yalnızca bir şekilde tartışın. Aksi takdirde, kullanıcıların doğrudan yaşayabilecek sistem davranışına ilişkin tartışmayı saklayın. Gereksinimler modelini mimari modelden ayrı tutun.

- Teknik olmayan hissedarlar genellikle, sizin için bazı kılavuzlarla birlikte UML diyagramlarını anlamak için sorun yaşalınmaz.

#### <a name="link-model-to-work-items"></a>Modeli Iş öğelerine bağlama
 Gereksinimler atölyinden sonra, gereksinimler modelinin ayrıntılarını ayrıntılandırma ve modeli geliştirme görevlerine bağlama. Bunu, [!INCLUDE[esprfound](../includes/esprfound-md.md)] iş öğelerini modeldeki öğelere bağlayarak yapabilirsiniz. Bunun nasıl yapılacağını öğrenmek için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).

 Herhangi bir öğeyi iş öğelerine bağlayabilirsiniz, ancak en yararlı öğeler aşağıdaki gibidir:

- Kullanım örnekleri. Bir kullanım örneğini, uygulamayı uygulayacak geliştirme görevlerine bağlayabilirsiniz.

- Kullanım örneği uzantıları. Bir yineleme içinde kullanım örneğinin yalnızca bir yönü uygulanırsa, bir veya daha fazla uzantıyla birlikte bir temel kullanım örneğine ayırabilirsiniz. Uzantılar, «Extend» ilişkisiyle birlikte taban durumuna bağlı olan kullanım durumlarıdır. Kullanım örneği uzantısı hakkında daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md).

- İş kurallarını veya hizmet kalitesi gereksinimlerinin kalitesini açıklayan açıklamalar. Daha fazla bilgi için bkz. [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

#### <a name="link-model-to-tests"></a>Modeli testlere bağlama
 Kabul testlerinin tasarımına kılavuzluk etmek için gereksinimler modelini kullanın. Bu testleri geliştirme işlerinde eşzamanlı olarak oluşturun.

 Bu teknik hakkında daha fazla bilgi edinmek için bkz. [bir modelden test geliştirme](../modeling/develop-tests-from-a-model.md).

#### <a name="estimate-remaining-work"></a>Kalan Işi tahmin etme
 Gereksinimler modeli, her yinelemenin boyutuyla ilgili olarak projenin toplam boyutunu tahmin etmenize yardımcı olabilir. Kullanım örneklerinin ve sınıflarının sayısını ve karmaşıklığını değerlendirmek, gereken geliştirme işini tahmin etmenize yardımcı olabilir. İlk birkaç yinelemeyi tamamladıktan sonra, ele alınan gereksinimlerin ve gereksinimlerin bir karşılaştırması projenin geri kalanının maliyeti ve kapsamının yaklaşık bir ölçümünü verebilir.

 Her yinelemenin sonuna yakın bir şekilde, gereksinimlerin gelecekteki yinelemelere atanmasını gözden geçirin. Kullanım durumu diyagramında bir alt sistem olarak her bir yinelemenin sonunda yazılımınızın durumunu göstermek faydalı olabilir. Tartışmalarda, bu alt sistemlerden birindeki kullanım örneklerini ve kullanım örneği uzantılarını diğerine taşıyabilirsiniz.

## <a name="levels-of-abstraction"></a>Soyutlama düzeyleri
 Modeller, yazılımla ilgili olarak bir soyutlama aralığına sahiptir. En somut modeller doğrudan program kodunu temsil eder ve en soyut modeller kodda gösterilebilen veya gösterilemeyen iş kavramlarını temsil eder.

 Bir model, çeşitli diyagramlar aracılığıyla görüntülenebilir. Modeller ve diyagramlar hakkında daha fazla bilgi için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

 Farklı türlerde diyagram, tasarımı farklı soyutlama düzeylerinde tanımlamak için faydalıdır. Birçok diyagram türü, birden fazla düzeyde yararlıdır. Bu tablo, her diyagram türünün nasıl kullanılabileceğini gösterir.

|Tasarım düzeyi|Diyagram türleri|
|------------------|-------------------|
|İş süreci<br /><br /> Sisteminizin kullanılacağı bağlamı anlamak, kullanıcıların ne ihtiyacı olduğunu anlamanıza yardımcı olur.|-Etkinlik diyagramları, iş hedeflerine ulaşmak için kişiler ve sistemler arasındaki iş akışını anlatmaktadır.<br />-Kavramsal sınıf diyagramları, iş sürecinde kullanılan iş kavramlarını anlatmaktadır.|
|Kullanıcı gereksinimleri<br /><br /> Kullanıcılarınızın sisteminizden ihtiyacı olan tanım.|-Kullanım örneği diyagramları, kullanıcıların ve diğer dış sistemlerin geliştirmekte olduğunuz sistemle olan etkileşimleri özetler. Her kullanım örneğine başka belgeler iliştirebilir ve bunu ayrıntılı olarak tanımlayabilirsiniz.<br />-UML sınıf diyagramları, kullanıcıların ve sistemin iletişim kurduğu bilgi türlerini anlatmaktadır.<br />-İş kuralları ve hizmet gereksinimlerinin kalitesi ayrı belgelerde açıklanabilir.|
|Yüksek düzey tasarım<br /><br /> Sistemin genel yapısı: ana bileşenler ve bunların nasıl birlikte kullanıldığı.|-Katman diyagramları sistemin birbirine bağlı parçalar halinde nasıl yapılandırıldığını açıklamaktadır. Mimariye uymasını sağlamak için program kodunu katman diyagramlarına karşı doğrulayabilirsiniz.<br />-Bileşen diyagramları, her bileşen için sunulan ve gereken iletileri ve Hizmetleri belirten parçaların arabirimlerini gösterir.<br />-Sıralı diyagramlar, bileşenlerin her kullanım durumunu uygulamak için nasıl iletişim kurduğunu gösterir.<br />-UML sınıf diyagramları, bileşenlerin arabirimlerini ve bileşenler arasında geçirilen veri türlerini anlatmaktadır.|
|Tasarım desenleri<br /><br /> Tasarımın tüm bölümlerinde kullanılan tasarım sorunlarını çözme kuralları ve yöntemleri|-UML sınıf diyagramları bir düzenin yapılarını anlatmaktadır<br />-Sequence veya Activity diyagramlarında etkileşimleri ve algoritmaları gösterir|
|Kod analizi<br /><br /> Koddan birkaç tür diyagram oluşturulabilir.|-Sıralı diyagramlar koddaki nesneler arasındaki etkileşimi gösterir.<br />-Katman diyagramları sınıflar arasındaki bağımlılıkları gösterir. Güncelleştirilmiş kod, katman diyagramına göre doğrulanabilir.<br />-Sınıf diyagramları, koddaki sınıfları gösterir.|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Köprü**|
|------------------|---------------|
|**Videolar**|![video MSDN 'ye bağlantı](../data-tools/media/playvideo.gif "PlayVideo") [: nasıl yapılır videoları: UML modellerini ve diyagramlarını oluşturma ve kullanma (Visual Studio 2010 Ultimate)](https://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![video](../data-tools/media/playvideo.gif "PlayVideo ") [kanalı 9 ' a bağlantı: Visual STUDIO 2010 ile UML](https://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![video MSDN bağlantısı](../data-tools/media/playvideo.gif "PlayVideo ") [nasıl yapılır: UML araçları ve genişletilebilirliği (Visual Studio 2010 Ultimate)](https://go.microsoft.com/fwlink/?LinkID=214467)|
|**Forumları**|-   [Visual Studio görselleştirme & modelleme araçları](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Bloglar**|[Visual Studio ALM + Team Foundation Server blogu](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Teknik makaleler ve Günlükler**|[MSDN mimari Merkezi](https://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Visual Studio Mimari Araç Kullanımı Kılavuzu](../modeling/visual-studio-architecture-tooling-guidance.md)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Çevik geliştirme içinde modelleri kullanma](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [uygulama](../modeling/create-models-for-your-app.md) [modelleriniz için model oluşturma kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [modeli uygulamanızın mimarisi](../modeling/model-your-app-s-architecture.md) , [modelleme çözümünüz model yapısından](../modeling/structure-your-modeling-solution.md) [Test geliştirme](../modeling/develop-tests-from-a-model.md)
