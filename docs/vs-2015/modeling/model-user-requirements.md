---
title: Kullanıcı gereksinimlerini modelleyin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f27fede436ea6cabe0aab6480cd4841299c42293
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302797"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, etkinlikleri hakkında diyagramlar çizerek kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışmanıza ve iletmenize yardımcı olur. Gereksinimler modeli, her biri kullanıcı gereksinimlerinin farklı bir yönüne odaklanan Bu diyagramların bir kümesidir. Video gösterimi için bkz. [Iş etki alanını modelleme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

 Hangi Visual Studio sürümlerinin her model türünü desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Gereksinim modeli şunları yapmanıza yardımcı olur:

- İç tasarımından ayrı olarak sistemin dış davranışına odaklanın.

- Doğal dilde olduğundan, kullanıcıların ve paydaşların ihtiyaçlarını çok daha az belirsizliğe göre tanıtın.

- Kullanıcılar, geliştiriciler ve test ediciler tarafından kullanılabilecek tutarlı bir terim sözlüğü tanımlayın.

- Gereksinimlerde boşlukları ve tutarsızlıkları azaltın.

- Gereksinim değişikliklerine yanıt vermek için gereken işi azaltın.

- Özelliklerin geliştirilecek sırayı planlayın.

- Testler ve gereksinimler arasında net bir ilişki yaparak modelleri sistem testleri için temel olarak kullanın. Gereksinimler değiştiğinde, bu ilişki testleri doğru şekilde güncelleştirmenize yardımcı olur. Bu, sistemin yeni gereksinimleri karşıladığından emin olmanızı sağlar.

  Bir gereksinim modeli, kullanıcıları veya temsilcileriyle tartışmalara odaklanmak için kullanıyorsanız en büyük avantaj sağlar ve her yinelemenin başlangıcında onu tekrar ziyaret edebilirsiniz. Kodu yazmadan önce ayrıntılı olarak doldurmanız gerekmez. Kısmen çalışan bir uygulama, çok fazla Basitleştirilmiş olsa bile, genellikle gereksinimlerle ilgili olarak gereksinimlerin tartışılması için en fazla bir temel oluşturur. Model, bu tartışmaların sonuçlarını özetlemek için etkili bir yoldur. Daha fazla bilgi için bkz. [geliştirme sürecinizdeki modelleri kullanma](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Bu konularda, "sistem", geliştirmekte olduğunuz sistem veya uygulama anlamına gelir. Birçok yazılım ve donanım bileşeninin büyük bir koleksiyonu olabilir; ya da tek bir uygulama; veya daha büyük bir sistem içindeki bir yazılım bileşenidir. Her durumda, gereksinimler modeli, bir kullanıcı arabirimi veya API aracılığıyla sisteminizin dışından görülebilen davranışı açıklar.

## <a name="common-tasks"></a>Ortak Görevler
 Kullanıcıların gereksinimlerinin birkaç farklı görünümünü oluşturabilirsiniz.  Her görünüm belirli bir bilgi türü sağlar.  Bu görünümleri oluşturduğunuzda sıklıkla bir tane diğerine taşımak en iyisidir. Herhangi bir görünümden başlayabilirsiniz.

|Diyagram veya belge|Gereksinimler modelinde neleri açıklar|Section|
|-------------------------|-----------------------------------------------|-------------|
|Kullanım örneği diyagramı|Sistemi kim ve bununla ne yaptığını kullanır.|[Sisteminizin nasıl kullanıldığını açıklama](#UseCases)|
|Kavramsal sınıf diyagramı|Gereksinimleri anlatmak için kullanılan türlerin sözlüğü; Sistem arabiriminde görünen türler.|[Gereksinimleri tanımlamak için kullanılan terimleri tanımlama](#RequirementsClasses)|
|Etkinlik diyagramı|Kullanıcılar ve sistem veya bölümleri tarafından gerçekleştirilen etkinlikler arasında iş ve bilgi akışı.|[Kullanıcılar ve sisteminiz arasındaki iş akışını gösterme](#Workflow)|
|Sıralı diyagram|Kullanıcılar ve sistem bölümleri arasındaki etkileşimler dizisi. Etkinlik diyagramına alternatif bir görünüm.|[Kullanıcılar ve sisteminiz arasındaki etkileşimleri gösterme](#Sequences)|
|Ek belgeler veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet gereksinimlerinin kalitesini açıklama](#QoSRequirements)|
|Ek belgeler veya iş öğeleri|Belirli bir kullanım örneğine özgü bulunmayan kısıtlamalar ve kurallar|[İş kurallarını gösterme](#BusinessRules)|

 Diyagram türlerinin çoğunun başka amaçlar için de kullanılabileceğini unutmayın. Diyagram türlerine genel bir bakış için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md). Diyagram çizme hakkında temel bilgiler için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

## <a name="UseCases"></a>Sisteminizin nasıl kullanıldığını açıklama
 Sistemi kimin kullandığını ve ne için kullandıkları hakkında açıklama için kullanım örneği diyagramları oluşturun. Kullanım örneği, bir sistem kullanıcısının hedefini ve hedefe ulaşmak için gerçekleştirdikleri yordamı temsil eder.

 Örnek olarak, bir çevrimiçi yemek satışı sistemi, müşterilerin bir menüden öğe seçmesine izin vermelidir ve bu, restoranların menüyü güncelleştirmesine izin vermelidir. Bunu, kullanım durumu diyagramında özetleyebilirsiniz:

 ![Müşteri ve restoran için kullanım örnekleri](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")

 Ayrıca, kullanım durumunun daha küçük durumlardan nasıl oluştuğunu de gösterebilirsiniz. Örneğin, yemek siparişi veren bir yemek satın alma parçasıdır ve bu da ödeme ve teslimi içerir:

 ![Sistem ödemeye katılıyorsa, ancak teslim edilmez.](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")

 Ayrıca, geliştirmekte olduğunuz sistem kapsamına hangi kullanım örneklerinin ekleneceğini de gösterebilirsiniz. Örneğin, çizimdeki sistem yemek sunma kullanım durumunda yer almaz. Bu, geliştirme işinin bağlamını ayarlamanıza yardımcı olur. (Kullanım durumu diyagramında, sistem veya bileşenlerini göstermek için alt sistem kapsayıcıları kullanılabilir.)

 Ayrıca, takımınızın birbirini izleyen sürümlerde nelerin dahil edileceğini tartışmanıza de yardımcı olur. Örneğin, sistemin ilk sürümünde yemek için ödeme, sistem aracılığıyla değil, Restoran ve müşteri arasında düzenlenip düzenlenmediğini tartışabilirsiniz. Bu durumda, ilk sürüm için şimdi akşam yemeği sistem dikdörtgeninin dışında yemek ödemesini taşıyabilirsiniz.

 Kullanım durumu diyagramı yalnızca kullanım örneklerinin bir özetini sağlar. Daha ayrıntılı açıklamalar sağlamak için diyagramdaki kullanım çalışmalarını, belgelere ve diğer diyagramlara bağlayabilirsiniz. Bunun nasıl yapılacağını öğrenmek için bkz. [kullanım örneğini belgelere ve diyagramlara bağlama](../modeling/link-a-use-case-to-documents-and-diagrams.md).

 Kullanım durumu diyagramı çizme takımınıza yardımcı olur:

- Uygulamanın ayrıntılarına odaklanmadan, kullanıcıların sistemle ne kadar durmayı beklediğini odaklanın.

- Sisteminizin kapsamını veya sistemin belirli sürümlerini tartışın.

  Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|Kullanım örnekleri oluşturma hakkında daha ayrıntılı bilgi|[UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|
|Kullanım durumu diyagramındaki öğeler|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|
|Kullanım çalışmalarından kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="RequirementsClasses"></a>Gereksinimleri tanımlamak için kullanılan terimleri tanımlama
 Aşağıdaki amaçlar için kullanılan iş kavramlarının tutarlı bir sözlüğünü geliştirmenize yardımcı olması için UML sınıf diyagramlarını kullanabilirsiniz:

- Kullanıcıların, sistemin çalıştığı işletmeyi tartışın.

- Kullanıcıların ihtiyaçlarını, örneğin kullanım örnekleri, iş kuralları ve Kullanıcı hikayeleri açıklamalarıyla ilgili olarak anlatmak için.

- Sistemin API 'sinde veya Kullanıcı arabirimi aracılığıyla değiştirilen bilgi türleri.

- Sistem veya kabul testlerinin açıklamaları.

  Bu amaçla kullanıldıkları zaman, bir UML sınıf diyagramının içeriğine kavramsal sınıf diyagramı adı verilir. (Bir *etki alanı modeli* veya *analiz sınıfı modeli*olarak da bilinir.)

  Kavramsal bir sınıf diyagramında, sistemin iç tasarımının ayrıntılarını göstermeden yalnızca gereksinimlerin açıklamalarında gerekli olan sınıfları gösterebilirsiniz. Diyagram, sistemin iç tasarımının ayrıntılarını göstermez. Genellikle kavramsal sınıflarda işlemler veya arabirimler gösterilmez.

  Örneğin, şimdi akşam yemeği sistemine yönelik bu kavramsal sınıfları çizebilirsiniz:

  ![Sınıflar menüsü, sırası, menü öğesi, sıralama öğesi.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")

  Kavramsal sınıf diyagramı, gereksinim modeli boyunca kullandığınız terimlerin sözlüğünü sağlar. Örneğin, bir yemek kullanım örneği sırasının ayrıntılı açıklamasında şunu yazabilirsiniz:

  Müşteri, *sipariş*oluşturmak Için bir *menü* seçer ve ardından *menüden* *menü öğeleri* ' ni *seçerek sırayla* *sipariş öğeleri* oluşturur.

  Bu açıklamada kullanılan terimlerin modeldeki sınıfların adları olduğunu fark edin. Diyagram, belirsizlikleri bu sınıflar arasındaki ilişkilerden kaldırır. Örneğin, her bir siparişin yalnızca bir menü ile ilişkilendirildiğini açıkça gösterir.

  Kullanıcıların gereksinimleriyle ilgili yanlış anlayışları, genellikle sözcüklerin ayrıntılı anlamları hakkında yanlış bir şekilde izlenebilir. Örneğin, çoğu Restoranlar, hüküm menüsü ve sırası ile paylaşılan bir anlama sahip olacaktır, ancak bir siparişte bulunan bir öğe ile menüdeki bir öğe arasındaki fark daha az net olur. Gereksinimler iş hissedarlarıyla ele alındığı zaman, bu farklılıkları göstermek önemlidir. Sınıf diyagramı, terimleri ve bunların ilişkilerini açıklığa kavuşturmanıza yardımcı olan yararlı bir araçtır.

  Kavramsal sınıf modeli, sisteminizin iş mantığının açıklanbileceği temel sözlük oluşturabilir. Ancak, uygulamanızın performans, dağıtım, esneklik ve diğer etkenler gibi sorunları düşünmesi gerektiğinden, yazılım içindeki sınıflar genellikle kavramsal modelden çok daha karmaşıktır. Kavramsal sınıfın birçok farklı uygulaması, tek bir sistemde sıklıkla bulunur.

  Örneğin, siparişler XML, SQL, HTML ve C# farklı sistem parçaları ve parçalar arasındaki farklı arabirimlerde gösterilebilir. Bir sipariş ve menü arasındaki ilişki, kod içindeki C# başvurular, bir veritabanındaki ILIŞKILER veya XML içindeki çapraz başvuru kimlikleri gibi birçok farklı yolla gösterilebilir. Ancak, bu farklılıklara rağmen kavramsal model, yazılımın her bölümünde doğru olan önemli bilgileri sağlar. Örnekteki sınıf diyagramı bize her uygulamada, her bir siparişle ilişkili yalnızca bir menü olacağını söyler.

  Gereksinimler sınıf diyagramı çizme takımınıza yardımcı olur:

- Kullanıcıların ihtiyaçlarına ait tartışmalarda kullanılan temel terimleri tanımlayın ve standartlaştırın.

- Bu terimler arasındaki ilişkileri açıklığa kavuşturun.

  Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|Gereksinim sınıfları bulma hakkında daha ayrıntılı bilgi|[UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Kavramsal sınıf diyagramındaki öğeler|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|
|Kavramsal sınıflardan kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

 Kavramsal bir sınıf diyagramında, genellikle gezinmelerin gezinebilmesini sağlamak için, ilişkilerin oklara yerleştirileceğini göstermek yararlı değildir. Bunun nedeni, diyagramın bir uygulamayı temsil etmez. İlişkilendirmeler gerçek dünya nesneleri arasındaki ilişkileri temsil eder. Aşağıdaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı, varsayılan olarak çift yönlü oklar yapar: [örnek: UML etki alanı modelleme özellikleri](https://go.microsoft.com/fwlink/?LinkId=213849).

## <a name="BusinessRules"></a>Iş kurallarını gösterme
 İş kuralı, belirli bir kullanım örneği ile ilişkilendirilmemiş ve sistem genelinde gözlenecek bir gereksinimdir.

 Birçok iş kuralı, kavramsal sınıflar arasındaki ilişkilerdeki kısıtlamalardır. Bu *statik iş kurallarını* , kavramsal sınıf diyagramında ilgili sınıflarla ilişkili açıklamalar olarak yazabilirsiniz. Örneğin:

 ![Açıklama, Order sınıfına iliştirilmiş kural.](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")

 *Dinamik iş kuralları* , izin verilen olay dizilerini kısıtlar. Örneğin, bir kullanıcının sisteminizde başka işlemler gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıra veya etkinlik diyagramı kullanın.

 Ancak, birçok dinamik kural, statik kurallarla değiştirilerek daha etkin ve genel olarak ifade edilebilir. Örneğin, kavramsal sınıf modelindeki bir sınıfa ' oturum açmış ' Boole özniteliği ekleyebilirsiniz. Oturum açma durumunu kullanım durumunun sonkoşulu olarak, diğer kullanım örneklerinin çoğunun bir önkoşulu olarak eklemeniz gerekir. Bu yaklaşım, olay sıralarının tüm olası birleşimlerini tanımlamaktan kaçınmanızı sağlar. Modele yeni kullanım durumları eklemeniz gerektiğinde de daha esnektir.

 Buradaki seçim, gereksinimlerin nasıl tanımladığına ilişkin olduğunu ve bu seçeneğin program kodunda gereksinimlerin nasıl uygulandığını fark ettiğini unutmayın.

 Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|Statik iş kurallarını bulma ve kaydetme hakkında daha ayrıntılı bilgi|[UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Kavramsal sınıf diyagramındaki öğeler|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|
|İş kurallarına uygun kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="QoSRequirements"></a>Hizmet gereksinimlerinin kalitesini açıklama
 Hizmet gereksinimi kalitesi için çeşitli kategoriler vardır. Bunlar aşağıdakileri içerir:

- Performans

- Güvenlik

- Kullanılabilirlik

- Güvenilirlik

- Sağlamlık

  Bu gereksinimlerin bazılarını, belirli kullanım durumlarının açıklamalarına dahil edebilirsiniz. Diğer gereksinimler kullanım örneklerine özgü değildir ve en etkili şekilde ayrı bir belgede yazılır. Mümkün olduğunda, gereksinim modeli tarafından tanımlanan bir sözlüğüne bağlı kalmak yararlı olur. Aşağıdaki örnekte, gereksinimde kullanılan ana sözcüklerin, önceki çizimlerdeki aktörlerin, kullanım durumlarının ve sınıfların başlıkları olduğunu fark edeceksiniz:

  Bir restoran, bir müşteri bir yemek sipariş ederken bir menü öğesini silerse, bu menü öğesine başvuran herhangi bir sıralama öğesi kırmızı renkte görüntülenir.

  Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|Kullanım örneklerine ek belgeler iliştirme|[Kullanım örneğini belgelere ve diyagramlara bağlama](../modeling/link-a-use-case-to-documents-and-diagrams.md)|
|Hizmet gereksinimlerinin kalitesi ile ilgili kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="Workflow"></a>Kullanıcılar ve sisteminiz arasındaki iş akışını gösterme
 Farklı kullanım örnekleri arasındaki iş akışını göstermek için bir etkinlik diyagramı kullanabilirsiniz. Kullanıcılara, hem sistemle hem de dışında gerçekleştirdiği ana görevleri gösteren bir etkinlik diyagramı çizerek bir gereksinim modeline başlamak sık sık yararlıdır.

 Örneğin:

 ![Üç eylem ve bir döngüyle etkinlik.](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")

 Aynı bilgilerin farklı görünümlerini göstermek için kullanım örneği diyagramları ve etkinlik diyagramları çizebilirsiniz.  Kullanım durumu diyagramı, daha küçük etkinliğin iç içe geçme durumunu göstermek için daha etkilidir, ancak iş akışını göstermez. Örneğin:

 ![Önceki eylemler için kullanım örnekleri](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")

 Ayrıca, yazılım içindeki algoritmaları betimlemek için etkinlik diyagramlarını da kullanabilirsiniz, ancak iş süreci için diyagramları kullandığınızda, sistem dışında görünür olan eylemlere odaklanırsınız.

 Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|İş iş akışlarının nasıl tanımlanacağı hakkında daha fazla bilgi|[UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|
|Etkinlik diyagramındaki öğeler|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|
|Etkinlik Diyagramlarından Kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="Sequences"></a>Kullanıcılar ve sisteminiz arasındaki etkileşimleri gösterme
 Sistem ve dış aktörler arasında veya sisteminizin bölümleri arasında ileti değişimi göstermek için sıralı diyagram kullanabilirsiniz. Bu, etkileşimlerin sırasını çok açık bir şekilde gösteren kullanım örneği içindeki adımların bir görünümünü sağlar. Sıralı diyagramlar özellikle, bir kullanım durumunda birkaç etkileşen taraf olduğu ve sisteminizin bir API 'nin bulunduğu yerlerde yararlıdır.

 Örneğin:

 ![Sistem ve aktör içeren sıralı diyagram.](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")

 Sıralı diyagramların bir avantajı, oluşturduğunuz sisteme hangi iletilerin geldiklerinden daha kolay bir avantajdır. Sistemi tasarlamak için, tek sistem yaşam çizgisini, bileşenlerinden her biri için ayrı bir yaşam çizgisi ile değiştirebilir ve sonra gelen her bir iletiye yanıt olarak bunlar arasındaki etkileşimleri gösterebilirsiniz.

 Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|--------------------|----------|
|Etkileşimlerin nasıl tanımlanacağı hakkında daha fazla bilgi|[UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Sıralı diyagramdaki öğeler|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|
|Dizi Diyagramlarından Kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="using-a-model-to-reduce-inconsistencies"></a>Tutarsızlıkları azaltmak için model kullanma
 Model oluşturma genellikle tutarsızlıklara ve kullanıcıların gereksinimlerine belirsizlikleri göre önemli bir azalmaya neden olur. Farklı hissedarlar genellikle sistemin çalıştığı iş dünyasının farklı yönlerini kullanır. Bu nedenle, ilk göreviniz istemcileriniz arasındaki bu farklılıkları çözvidir.

 Bir model oluştururken iş etki alanı ile ilgili birçok soruyu doğal olarak ortaya bir şekilde görürsünüz. Bu soruları kullanıcılarınıza yerleştirerek, projedeki daha sonraki bir aşamada değişiklik gereksinimini azaltacaksınız. İlk olarak kendinize sorabileceğiniz bazı özel sorular aşağıda verilmiştir ve yanıt net değilse iş hissedarlarına sorabilirsiniz:

- Gereksinim modelindeki her sınıf için, "hangi kullanım örneği bu sınıfın örneklerini oluşturuyor?" i sorun. Örneğin, çevrimiçi bir yemek siparişi hizmetinde, "ne tür kullanım örneği restoran menü sınıfının örneklerini oluşturuyor?" sorabilirsiniz. Bu, yeni bir restorana hizmetin nasıl imzalandığına ilişkin bir tartışmaya yol açabilir ve menüsüne katkıda bulunur. Öznitelikleri ve ilişkilendirmeleri oluşturan veya değiştiren şeyler hakkında benzer sorular sorabilirsiniz.

- Gereksinim modelindeki her kullanım örneği için, sınıf diyagramları tarafından sunulan sözcüklerdeki her kullanım durumunun sonucunu veya sonkoşullarını açıklamaya çalışın. Kullanım durumunun bir örneğinden önce ve sonra sınıfların örneklerini taslağı yaparak kullanım durumunun etkisini göstermek genellikle yararlı olur. Örneğin, kullanım durumu sonkoşulu, "müşterinin sırasına bir menü öğesi eklendiğinde, sipariş ve menü öğesi sınıflarının taslak örneklerini" belirtir. Yeni bir bağlantı veya yeni bir nesne gibi kullanım durumunun etkilerini, farklı bir renkte veya yeni bir çizimde gösterin. Bu, genellikle modelde hangi bilgilerin gerekli olduğu hakkında tartışmalara yol açar. Gereksinim sınıfları doğrudan uygulamayla ilgilenmese de, sisteminizin depolamak ve iletmek için ihtiyaç duyduğu bilgileri anlatmaktadır.

- Öznitelikler ve İlişkilendirmelerde kısıtlamalar hakkında, özellikle birden fazla öznitelik veya ilişkilendirme içeren kısıtlamalar hakkında sorun.

- Geçerli ve geçersiz kullanım örneği dizileri, çizim sırası veya etkinlik diyagramları hakkında bilgi ister.

  Farklı diyagramların sağladığı görünümler arasındaki ilişkileri inceleyerek kullanıcılarınızın iş yaptığı ana kavramları hızlıca anlayabilir ve bu kullanıcılara, sistemden ne ihtiyacı olduğunu anlamalarına yardımcı olabilirsiniz. Ayrıca, paydaşların en az hangi gereksinimlerle ilgili olduğunu daha iyi anlayabilirsiniz. Bu özellikleri, en az Basitleştirilmiş biçimde, projenin erken bir aşamasında, kullanıcıların bunları deneymelerine izin verecek şekilde geliştirmeyi planlarsınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [bir modelden test](../modeling/develop-tests-from-a-model.md) [Geliştirme Geliştirme işlem modelinizdeki modellerı kullanın](../modeling/use-models-in-your-development-process.md) [uygulamanızın mimarisi](../modeling/model-your-app-s-architecture.md) [örnek VS uzantısı: UML etki alanı modelleme özellikleri](https://go.microsoft.com/fwlink/?LinkId=213849) [örnek vs uzantısı: stereotipe göre](https://go.microsoft.com/fwlink/?LinkID=213841) UML öğeleri örnek vs uzantısı: UML öğelerini [bir uml diyagramına](https://go.microsoft.com/fwlink/?LinkID=213809) [bağlama](https://go.microsoft.com/fwlink/?LinkID=213813) [video: iş etki alanını modelleme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)
